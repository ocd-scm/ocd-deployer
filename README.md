# ocd-deployer

If you are practicing 12factor.net then all you need is to set the container image, the number of replicas, and the list of `ConfigMap`s and `Secret`s to map as enviroment variables, and your are done. Naturally you also need a service and a route to expose the app but that is simply boilerplate. 

This means that there can be "one generic chart to rule all microservices". Helmfile is the perfect engine to cookie cutter stamp out multiple microservices from simple yaml in your git repo that provides the list of secrets and configmaps to mount. 

It would be very straight forward to parameterize persistent volumes for storage into this generic chart. Yet stateful apps are an antipattern in 12factor.net. You should configure a cloud-native managed persistent storage such as S3 buckets (or Azure Blog, or Google Cloud Storate) and use a cloud native database service (AWS RDS, Azure Postres, Google Cloud SQL, compose.com, ...).  Disclosure: We do run Redis instances with PVCs but only for temporary data so there is no backup and restores. 

## See Also

The [ocd-meta wiki](https://github.com/ocd-scm/ocd-meta/wiki)

https://github.com/ocd-scm/ocd-builder
