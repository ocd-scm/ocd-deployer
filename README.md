# ocd-deployer

If you are practicing 12factor.net then there can be "one generic chart to rule all microservices". All you need to supply this chart is: 

 1. The container image and tag
 2. The number of replicas
 3. An optional list of enviroment variables (not shared with other deployments)
 4. An optional list of configmaps to mount as environent variables (shared with other deployments)
 3. An optional list of secrets to mount as enviroment variables (changed independently, possibly shared with other deployments)

It will generate the deployment as well as a service and a route to expose the app. 

Helmfile is the perfect engine to cookie cutter stamp out multiple microservices from simple yaml in your git repo. Use the OCD enviroment webhook project to refresh your microservices whenever you update helmfile.yaml in your git repo. 

This chart does not supply persistent volumes for storage as stateful apps are an antipattern in 12factor.net. You should configure a cloud-native managed persistent storage such as S3 buckets (or Azure Blog, or Google Cloud Storage) and use a cloud native database service (AWS RDS, Azure Postres, Google Cloud SQL, compose.com, ...).  Disclosure: We do run Redis instances in openshift with PVCs but only for temporary data so there is no backup and restores. 

## See Also

The [ocd-meta wiki](https://github.com/ocd-scm/ocd-meta/wiki)

https://github.com/ocd-scm/ocd-builder
