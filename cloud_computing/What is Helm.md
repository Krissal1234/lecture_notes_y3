 helm has a couple of main feature
- it is a package manager for kubernetes, to package yaml files


helm charts are bundles of yaml files
- they can be pushed into a helm repository

you can download and use existing ones

commonly used deployments like database apps that have complex setups all have helm charts

there are also private registries for companies


Another funcationality for helm is that it is a templating engine
- if  you have multiple microservices with the only change to be a couple of values, you can define a common blueprint and have a template file with variables 


Helm chart structure

- mychart
	- Chart.yaml - meta info about charts
	- values.yaml  - values for the template files ( default values you can override later)
	- charts/ - chart dependencies 
	- templates/ - template files are installed`


Value injection into template files
values.yaml
- the default values here can be overwritten
