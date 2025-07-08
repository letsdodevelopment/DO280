# How to use web_appy to learn declarative approach?

First, run the oc create command to validate yaml file as shown below

```bash
oc create -f . --validate=true --dry-run=server

### \/ output \/ ###
# deployment.apps/httpd24-app created (server dry run)
# route.route.openshift.io/httpd24-rt created (server dry run)
# service/httpd24-svc created (server dry run)

### /\ output /\ ###
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

