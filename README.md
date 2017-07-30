## Description

Official Kibana image + removed xpack, tested on Openshift origin.

To upgrade/downgrade version change the version.txt file

Documentation can be found on the [Elastic web site](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html).

**Make sure you have read all the instructions properly, just "skimming through" will not help you.**

## Running on Openshift
```
make
docker tag docker.elastic.co/elasticsearch/elasticsearch:5.5.0 172.30.1.1:5000/myproject/elasticsearch:5.5.0
docker push 172.30.1.1:5000/myproject/elasticsearch:5.5.0
oc new-app --image-stream=elasticsearch:5.5.0
```
### In case you experience "Permissions Denied" issues 
```
oadm policy add-scc-to-user anyuid system:serviceaccount:myproject:default
oadm policy add-scc-to-group anyuid system:serviceaccount:myproject:default
```

## Supported Docker versions

The images have been tested on Docker 17.03.1-ce.

## Requirements

A full build and test requires:

- Docker
- GNU Make
- Python 3.5 with Virtualenv

## Contributing, issues and testing

Acceptance tests for the image are located in the test directory, and can be invoked with `make test`.

This image is built on [CentOS 7](https://github.com/CentOS/sig-cloud-instance-images/blob/CentOS-7/docker/Dockerfile).
