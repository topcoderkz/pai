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
* The [metrics] from Prometheus service are extended and data can be exported per job, node or service.
* A new patch [docker-executor](./src/hadoop-ai/build/docker-executor.patch) is added to hadoop-ai and Yarn node manager will run all applications in docker containers.
* OpenPAI services use node affinity to select the nodes to deploy - [PR 1081](https://github.com/Microsoft/pai/pull/1081).
* Etcd data path configuration entry is added to [Kubernetes Configuration](./deployment/quick-start/kubernetes-configuration.yaml.template) and user can configure the path to store etcd data permanently - [PR 1221](https://github.com/Microsoft/pai/pull/1221).

## Bug Fixes
* Fix namespace when submitting job in yaml format - [ PR 1438 ](https://github.com/Microsoft/pai/pull/1438)
* Fix job exporter to update the metric file event if no metrics got. Readiness probe requires this to check the file's modification time - [PR 1268](https://github.com/Microsoft/pai/pull/1268).

## Known Issues

## Break Changes
