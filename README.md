# Pipelines End-End Demo

## Pre-requisites
1. Openshift Cluster - You can use https://www.redhat.com/sysadmin/codeready-containers
2. Follow [Openshift Pipelines Operator](https://docs.openshift.com/pipelines/latest/about/understanding-openshift-pipelines.html) installation steps to install Openshift Pipelines  

**Demo:** How easily cronJobs can be converted to Openshift Pipelines

**Scenario:** 

We have the following jobs:

1. cronJob to fetch data from a particular source and store it into a PVC.
2. cronJob to convert fetched data into CSV
3. cronJob to read data from storage

Now let's use the Openshift Pipelines to streamline our cloud workloads.

**Note:** Demo assumes that he/she has knowledge about Openshift Pipelines and how to execute the resources.

## Let's start

* Demo covers 
  1. How to re-use the tasks
  2. results
  3. runAfter (To manage task run)
  4. when expression(if/else)
  5. finally(cleanup/removal)
  6. workspaces(storage)
  7. params(how data can be passed from one place and used in multiple places)


1. Create a project
```
oc new-project demo
```
2. Create reusable task from hub.tekton.dev
```
oc create -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/write-file/0.1/write-file.yaml
```
3. create the pipeline and task that are required for the demo
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
    
The final demo looks like below

![Screenshot from 2023-04-20 17-28-21](https://user-images.githubusercontent.com/9441662/233359312-43ba84ef-0d71-4e73-8aef-5985ff70cfd7.png)

![Screenshot from 2023-04-12 16-11-53](https://user-images.githubusercontent.com/9441662/231434347-55eb36c7-607a-4215-9824-b5f7b7f24177.png)


