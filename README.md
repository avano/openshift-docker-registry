# openshift-docker-registry
Custom docker registry in OpenShift with configured certificates

# Deploy

```
oc new-project <your project>
oc create -f template.yml
oc new-app registry -p PVC_CAPACITY=<int>Gi -p APP_NAME=<appname> -p DOCKER_IMAGE=<dockerimage>
```

You can then create a port-forward to the created service with:

```
oc port-forward svc/<appname> <your port>:443
```

In the cluster, you can reference the pushed docker image through the service using internal DNS:

```
<appname>.<namespace>.svc.cluster.local/<imagenamespace>/<imagename>:<imagetag>
```
