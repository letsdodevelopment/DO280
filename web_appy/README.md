# How to use web_appy to learn declarative approach?

First, run the oc create command to validate yaml file as shown below

```bash
oc create -f . --validate=true --dry-run=server

### \Ü/ output \Ü/ ###
# deployment.apps/httpd24-app created (server dry run)
# route.route.openshift.io/httpd24-rt created (server dry run)
# service/httpd24-svc created (server dry run)

### /Ü\ output /Ü\ ###
```

Second, run the oc create command

```bash
oc apply -f .
### \ö/ output \ö/ ###
deployment.apps/httpd24-app created
route.route.openshift.io/httpd24-rt created
service/httpd24-svc created
### /ö\ output /ö\ ###
```

## v1

This is v1 of the app which some changes in the http24_app.yaml files esp number of replicas

Third, ideally you should clone the branch web_apply_v1 but in this case, i will switch to branch web_appy_v1 and check what is changed using the git diff command

```shell
git diff .
### \ö/ output \ö/ ###
diff --git a/web_appy/README.md b/web_appy/README.md
index 488518b..e0bd274 100644
--- a/web_appy/README.md
+++ b/web_appy/README.md
@@ -24,3 +24,4 @@ service/httpd24-svc created

```text
+This is v1 of the app which some changes in the http24_app.yaml files esp number of replicas
\ No newline at end of file
diff --git a/web_appy/httpd24_app.yaml b/web_appy/httpd24_app.yaml
index 644a2e6..0132cc0 100644
--- a/web_appy/httpd24_app.yaml
+++ b/web_appy/httpd24_app.yaml
@@ -10,7 +10,7 @@ metadata:
     app: httpd24-app
   name: httpd24-app
 spec:
-  replicas: 6 # previous
+  replicas: 3 # v1 it is reducing the count to three
   selector:
     matchLabels:
       app: httpd24-app
### /ö\ output /ö\ ###
```

When you are satisfied with the change, simply go ahead and apply the change.

```shell
oc apply -f .
### \ö/ output \ö/ ###
deployment.apps/httpd24-app configured # confirms the change is implemented
route.route.openshift.io/httpd24-rt unchanged
service/httpd24-svc unchanged
### /ö\ output /ö\ ###
```
