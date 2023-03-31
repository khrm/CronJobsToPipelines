# Pipelines End-End Demo

## Pre-rquisites
1. Openshift Cluster
2. Follow [Openshift Pipelines Operator](https://docs.openshift.com/container-platform/4.12/cicd/pipelines/installing-pipelines.html#op-installing-pipelines-operator-in-web-console_installing-pipelines) installation steps to install Openshift Pipelines  

**Demo:** How easily cronJobs can be converted to Openshift Pipelines

**Scenario:** 

We will have couple of cronJobs

1. cronJob to create data and write to a perticular storage
2. cronJob checks storage to indicate existance of data
3. cronJob to read data from storage
4. cronJob to delete the data from storage/ cleanup the storage

Now lets use Openshift Pipelines concept to convert multipl cronJobs to achieve the usecase

**Note:** Demo assumes that he/she have knowledge about Openshift Pipelines and how to execute the resources.

## Lets start

* Demo uses `write-file` tasks from [hub.tekton.dev](https://hub.tekton.dev/)
* Demo covers results, runafter, when expression(if/else), finally(cleanup/removal), workspaces(storage), task reusability, params(how data can be passed from one place and used in multiple places)

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
