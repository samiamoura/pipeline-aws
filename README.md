# Pipeline CI/CD with full AWS environment 

## Build status badge

![Build Status](https://codebuild.eu-west-3.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoibE54YVNDYytzMUo1WlRxcVhJWG1SR0IyeXRSSVBpUTU3MWxGWWRLelBjVHZ1Wkk4RDJYcjVQam9KLzdvNWV1THF4ZE16Vmo1RVRnNkRSOVJpUDYxYnJ3PSIsIml2UGFyYW1ldGVyU3BlYyI6InRObHlWK2lJWnp0R0sxbjMiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)

## Tools

* Docker 
* AWS CodePipeline
* AWS CodeCommit 
* AWS Elastic Container Registry
* AWS Elastic Container Service
  + Clutser 
  + Service
  + Task
  
## Project 

The objective of this project is to deploy nodejs application using Docker engine and multiple AWS serivices.

## Files 

+ Application Source code is stored in [app](https://github.com/samiamoura/pipeline-aws/tree/master/app "app") folder
+ [Dockerfile](https://github.com/samiamoura/pipeline-aws/blob/master/Dockerfile "Dockerfile") is multiple step to build image
+ [buildspec.yml](https://github.com/samiamoura/pipeline-aws/blob/master/buildspec.yml "buildspec.yml") is file used by AWS and define multiple steps to build and push Docker image in the Elastic Container Registry
 

## Workflow

+ Source code is stored in CodeCommit
+ When source code is updated with push event, the pipeline is triggered. Below the list of diffents stage of pipeline.
  + Build: 
    + AWS use buildspec.yml file to build the image with the Dockerfile
  + Push:
    + Docker image is pushed in Elastic Container Registry
  + Deploy:
    + Docker image is used to run a container in the Elastic Container Service
+ Nodejs application is reachable with the Public IP (Elastic Network interface):
  + [http:**ElasticNetwork interface**:**exposedContainerPort**](# "http:<Elastic Network interface>:<exposedContainerPort>")
  
  
 
 ### View AWS Pipeline stpes 
 
 ![steps codepipeline](https://user-images.githubusercontent.com/58267422/80127612-ddbc9880-8594-11ea-9646-89ab8e03aad3.png)
 
 ### App Node.js
 
 ![applinodejs](https://user-images.githubusercontent.com/58267422/80127751-1197be00-8595-11ea-84f1-b601921cc1f3.png)

 
 
