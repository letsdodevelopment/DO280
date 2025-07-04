# Readme

The reason to create README is explain what is here and how I have used it.

etherpad repo are added as shown below

```shell
~/D/o/D/h/etherpad ❯❯❯ helm repo list                                                                                                                                                                                                                   main ⬆
NAME         	URL
redhat-cop   	https://redhat-cop.github.io/helm-charts
nicholaswilde	https://nicholaswilde.github.io/helm-charts/
```

## Step: 01

You always check what versions of Helm charts and app are availabel

```shell
helm search repo redhat-cop/etherpad --versions
NAME              	CHART VERSION	APP VERSION	DESCRIPTION
redhat-cop/etherpad	0.0.8        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.7        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.6        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.5        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.4        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.3        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.2        	latest     	A Helm chart for etherpad lite
redhat-cop/etherpad	0.0.1        	latest     	A Helm chart for etherpad lite
```

>Note: App and Chart version column

## Step:02

You always check what are the values one can define using the following command.

```shell
helm show values redhat-cop/etherpad --version 0.0.6
```

I have customized the chart using the files in values.yaml and values2.yaml.

values.yaml file has values which are aligned with nicholaswilde/etherpad chart and

values2.yaml is aligned with redhat-cop/etherpad.

## Upgrading chart

you can upgrade the chart in other words, the chart version.

```shell
helm upgrade etherv0061 redhat-cop/etherpad --version 0.0.8 -f values2.yaml

# check the history of upgrade

helm history etherv0061

REVISION	UPDATED                 	STATUS    	CHART         	APP VERSION	DESCRIPTION
1       	Thu Jul  3 15:40:40 2025	superseded	etherpad-0.0.6	latest     	Install complete
2       	Thu Jul  3 17:30:29 2025	superseded	etherpad-0.0.6	latest     	Upgrade complete
3       	Thu Jul  3 17:30:36 2025	deployed  	etherpad-0.0.8	latest     	Upgrade complete
```
