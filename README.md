# [kPow for Apache Kafka®](https://kpow.io) 
## Evaluate locally with Docker Compose

The following steps will start a 3-node Kafka cluster on your machine with Docker Compose and connect the latest version of kPow to that Kafka cluster with a 30-day trial licence that you have [obtained from our site](https://kpow.io/try/).

kPow will run with any Kafka Cluster from v1.0+ and is also [available as a JAR file](https://kpow.io/releases) for those without Dockerized environments. 

kPow also manages Schema Registries, Kafka Connect clusters, support a slew of enterprise integrations like User Authentication and RBAC, and runs with as little as ***256MB*** of memory and ***0.25CPU*** for a small installation. Our recommended installation is ***1GB/0.5CPU***.

Contact sales@operatr.io to upgrade your trial license to a fully featured 1-month Pro license if to evaluate User Authentication, Role Based Access Control, Data Policies, Prometheus Endpoints and more.

See our [User Guide](https://docs.kpow.io) for full documentation, this is the simplest configuration.

### To run kPow locally against a Dockerized 3-node Apache Kafka® cluster:

## Instructions

1. **CLONE** this repository.

```bash
git clone https://github.com/operatr-io/kpow-local.git
```

2. [Get a free, 30-Day trial license](https://kpow.io/try/).

3. **CHANGE** to the cloned directory

```bash
cd kpow-local
```

4. **EDIT** local.env and add your trial license details

```bash
vi local.env
```

5. **START** a new 3-node containerized Kafka cluster with a network named 'kpow_default'

```bash
docker-compose -p kpow up
```

6. **START** kPow with the same Docker network and the correct local environment settings.

```bash
docker run --network=kpow_default -p 3000:3000 -m1G --env-file ./local.env operatr/kpow:latest
```

7. **VIEW** kPow on http://localhost:3000. 

**Note:** kPow takes **two minutes** to initialize state on firt startup.

![kPow Starting](resources/screen-resources.png?raw=true)

8. **NOTE** The Kafka brokers are accessible on localhost:9092/9093/9094 if you want to configure other services.
-----

Any issues? Just [raise a ticket](https://github.com/operatr-io/community/issues).

Copyright © Operatr.IO 2020.
