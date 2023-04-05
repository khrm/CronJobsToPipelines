# Pipelines End-End Demo

## Pre-rquisites
1. Openshift Cluster
2. Follow [Openshift Pipelines Operator](https://docs.openshift.com/container-platform/4.12/cicd/pipelines/installing-pipelines.html#op-installing-pipelines-operator-in-web-console_installing-pipelines) installation steps to install Openshift Pipelines  

**Demo:** How easily cronJobs can be converted to Openshift Pipelines

**Scenario:** 

We will have couple of cronJobs

1. cronJob to fetch data from perticular source and store into perticular storage
2. cronJob to convert fetched data into CSV
3. cronJob to read data from storage

Now lets use Openshift Pipelines concept to convert multipl cronJobs to achieve the usecase

**Note:** Demo assumes that he/she have knowledge about Openshift Pipelines and how to execute the resources.

## Lets start

* Demo covers 
  1. How to re-use the tasks
  2. results
  3. runafter (To manage task run)
  4. when expression(if/else)
  5. finally(cleanup/removal)
  6. workspaces(storage)
  7. params(how data can be passed from one place and used in multiple places)


1. Create project
```
oc new-project demo
```
2. Create re usable task from hub.tekton.dev
```
oc create -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/write-file/0.1/write-file.yaml
```
3. create pipeline and task which are required for demo
```
oc create -f https://raw.githubusercontent.com/savitaashture/unicredit/main/examples/pipeline.yaml
```
4. create pipelinerun manually
```
oc create -f https://raw.githubusercontent.com/savitaashture/unicredit/main/examples/pipelinerun.yaml
```

5. re-create pipelinerun from console with single click

6. Create pipelinerun dynamically based on some events using
    
    * Pipelines as Code
    * Triggers
    
Final demo looks like below

![Screenshot from 2023-03-31 16-15-48](https://user-images.githubusercontent.com/9441662/229100341-572d0c1c-d800-4857-aa30-1d386e96c91c.png)
