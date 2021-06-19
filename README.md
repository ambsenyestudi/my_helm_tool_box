# my_helm_tool_box

## How start undestaing helm
Let's start by [Creating your first helm template](https://v2.helm.sh/docs/chart_template_guide/#a-starter-chart). 
After that as suggested in the link we will delete al template related things and star from scratch

## Your first templated varialbe

As seen on the link above lets create a *_helpers.tpl* but instead of a *configmap* I will go with *cronjob.yaml* (that works just as well).
Once created let's take the first four lines of the deployment.yaml crated by default this contain metadata an we’ll use it to setup the name form the Chart.yaml
```
apiVersion: apps/v1
kind: CronJob
metadata:
  name: {{ include "my-first-application.fullname" . }}
```
In this case we named the variable as **app.name** at *_helpers.tpl* so we will have to go form **my-first-application.fullname** to app name.

To check that everything works got your repository root directory and run the following command
> helm template [whatever_name] -f .\values.yaml

If all checks out you should se tha name devined at Chart.yaml as your metadata name.

```
//Chart.yaml
apiVersion: v2
name: my-first-application
```

