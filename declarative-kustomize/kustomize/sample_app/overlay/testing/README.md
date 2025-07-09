# sample_app_v1

In testing, I have adjusted the following

namePrefix=v1
Label: env: testing

As a effect name of the deploy, svc and route changes as per the prefix v1-

```bash
oc get all -l env=testing
###/öö\ Öutput /öö\ ###

NAME                                       READY   STATUS    RESTARTS   AGE
pod/v1-httpd24-app-test-75c5476957-4pngc   1/1     Running   0          3h29m
pod/v1-httpd24-app-test-75c5476957-fgx56   1/1     Running   0          3h29m
pod/v1-httpd24-app-test-75c5476957-gj6x8   1/1     Running   0          3h29m
pod/v1-httpd24-app-test-75c5476957-nfgkk   1/1     Running   0          3h29m
pod/v1-httpd24-app-test-75c5476957-tv5vb   1/1     Running   0          3h29m
pod/v1-httpd24-app-test-75c5476957-wncz9   1/1     Running   0          3h29m
pod/v1-httpd24-app-test-75c5476957-z9lrz   1/1     Running   0          3h29m

NAME                     TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
service/v1-httpd24-svc   ClusterIP   10.217.4.226   <none>        8080/TCP   3h29m

NAME                                  READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/v1-httpd24-app-test   7/7     7            7           3h29m

NAME                                             DESIRED   CURRENT   READY   AGE
replicaset.apps/v1-httpd24-app-test-75c5476957   7         7         7       3h29m

NAME                                     HOST/PORT                  PATH   SERVICES      PORT   TERMINATION   WILDCARD
route.route.openshift.io/v1-httpd24-rt   myhttpd.apps-crc.testing          httpd24-svc   8080                 None
###\öö/ Öutput \öö/ ###
```

## Patch file or patch content

In the development folder, you will simple example of using patch inside a kustomization.yaml file. It is bit complicate to write and remember
But if you compare that with the kustomization in the testing folder, one point the patch to the path in a file. The kustomization

```yaml kustomization.yaml
kind: Kustomization
namespace: sampleapp
namePrefix: v1-
commonLabels:
  env: testing
resources:
  - ../../base
patches:
  - path: patch.yaml
    target:
      kind: Deployment
      name: httpd24-app
    options:
      allowNameChange: true
```

And inside the patch.yaml file, the manifest file is exactly like any deployment manifest file.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd24-app-test
spec:
  replicas: 7
```
