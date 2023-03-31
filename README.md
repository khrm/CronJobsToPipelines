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

### Manually creating Pipeline and Pipelinerun

1. 


