## Source to Image Deployments

OpenShift allows developers to deploy applications without having to understand Docker and Kubernetes in depth. Similarly to the Cloud Foundry 'cf push' experience, developers can deploy applications easily via terminal commands and without having to build Docker images. In order to do this [Source-to-Image](https://github.com/openshift/source-to-image) is used.

## What is Source-to-image ?

<kbd><img src="images/image1.png" /></kbd>

Source-to-Image (S2I) is a toolkit for building reproducible container images from source code. 

S2I produces ready-to-run images by injecting source code into a Docker container and letting the container prepare that source code for execution.

By creating self-assembling builder images, you can version and control your build environments exactly like you use Docker images to version your runtime environments

In order to use S2I, builder images are needed. These builder images create the actual images with the applications. The builder images are similar to Cloud Foundry buildpacks.

The main advantage of using S2I for building reproducible Docker images is the ease of use for developers.

In this exercise, you will deploy a simple "Hello World" Node.js application.

### Step 1. Get the environment for the lab

URL: https://www.katacoda.com/openshift/courses/playgrounds/openshift311

S2I Lab: Here Source Code is https://github.com/IBMDevConnect/node-hello

And the Builder Image here is node.js version 8

### Step 2. Run the below command for S2I deployment

```
oc new-app -i=nodejs:8 https://github.com/IBMDevConnect/node-hello --name=node-hello

```

### Step 3. To verify your service is created:

Verify Service

```
oc get svc
```

### Step 4. Create a route.

```
$ oc expose svc node-hello
```

```
$ oc get route
```

### Step 5. Test the application

```
curl node-hello-default.2886795277-80-cykoria05.environments.katacoda.com
```

### Step 6. View the pods

```
oc get pod
```

Congratulations! You have completed this workshop!
