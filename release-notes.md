# Release v0.8.1

## New Features
* A clone button is added for running or failed jobs so user can resubmit those jobs with same configuration - [PR 1448](https://github.com/Microsoft/pai/pull/1448)
* [Marketplace and Submit job v2](./docs/marketplace-and-submit-job-v2/marketplace-and-submit-job-v2.md) feature allows users to share job templates, images, data, code and etc. across teams. 
* [paictl](./docs/paictl/paictl-manual.md) is extended to support configuration from external storage.
* The cleaner daemonset is added to remove the docker cache and check if there are dangling file handlers hold by live processes.
* ACL is enabled when accessing jobs via [RestAPI](./docs/rest-server/API.md).
* When logging in machines in the cluster, besides username and password, users can configure the ssh key file path for authentication. The details can be found in [deployment configuration](./docs/pai-management/doc/cluster-bootup.md).
* Prometheus service supports to mute alerts. The instructions can be found via [alert-manager](./docs/alerting/alert-manager.md#muting-firing-alert).

## Improvements
* Add [auto test](./examples/auto-test/readme.md) to run all the examples in a automatic or semi-automatic way.
* Memory limits are added for all OpenPAI services. Please refer [Resource Requirement](https://github.com/Microsoft/pai/wiki/Resource-Requirement) for details.
* When starting container to run user command, --init option is enabled to help avoiding zombie processes. - [PR 1435](https://github.com/Microsoft/pai/pull/1435)
* In the container running user's command, the code directory is mounted as readonly. - [PR 1422](https://github.com/Microsoft/pai/pull/1422)
* The job's view page is enhanced to contain the retry history link - [PR 1425](https://github.com/Microsoft/pai/pull/1425)
* In job submission request, both user specified and random ports are supported and they can coexist - [PR 1402](https://github.com/Microsoft/pai/pull/1402)
* OpenPAI source folder has a new structure and build facility is refactored out from [paictl](./docs/pai-management/README.md) and is implemented by [pai-build](./docs/pai-build/pai-build.md). 
* The [metrics](./docs/alerting/exporter-metrics.md) from alerting service are extended and metrics can be reported per job, node or service.
* A new patch [docker-executor](./src/hadoop-ai/build/docker-executor.patch) is added to hadoop-ai and Yarn node manager will run all applications in docker containers.
* OpenPAI services use node affinity to select the nodes to deploy - [PR 1081](https://github.com/Microsoft/pai/pull/1081).
* Etcd data path configuration entry is added to [Kubernetes Configuration](./deployment/quick-start/kubernetes-configuration.yaml.template) and user can configure the path to store etcd data permanently - [PR 1221](https://github.com/Microsoft/pai/pull/1221).
* When Yarn node manager service is deleted, the job containers will be cleaned - [PR 1296](https://github.com/Microsoft/pai/pull/1296).
* Alert email is refined for clarity - [PR 1282](https://github.com/Microsoft/pai/pull/1282).
* When starting kubelet, the docker root directory can be retrieved on the fly and it removes the restriction to fix the path to /var/lib/docker - [PR 1230](https://github.com/Microsoft/pai/pull/1230).
* Alert manager is enhanced to tolerate the disk and memory pressure of Kubernetes - [PR 1317](https://github.com/Microsoft/pai/pull/1317).


## Bug Fixes
* Fix namespace when submitting job in yaml format - [ PR 1438 ](https://github.com/Microsoft/pai/pull/1438)
* Fix job exporter to update the metric file event if no metrics got. Readiness probe requires this to check the file's modification time - [PR 1268](https://github.com/Microsoft/pai/pull/1268).
* Tensorflow version in Keras example is upgraded to 1.10 for compatibility - [PR 1130](https://github.com/Microsoft/pai/pull/1130).
* Fix the Zookeeper metrics export port - [PR 1192](https://github.com/Microsoft/pai/pull/1192).
* Fix [issue 1153](https://github.com/Microsoft/pai/issues/1153) by checking API resources before installing kube-proxy [PR 1210](https://github.com/Microsoft/pai/pull/1210).
* Fix [issue 1226](https://github.com/Microsoft/pai/issues/1226) and limit the image pull time in 10 minutes [PR 1227](https://github.com/Microsoft/pai/pull/1227).
* Fix [issue 1217](https://github.com/Microsoft/pai/issues/1217) to rotate exporter's log via docker daemon [PR 1239](https://github.com/Microsoft/pai/pull/1239).
* 

## Known Issues

## Break Changes
