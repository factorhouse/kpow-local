# Run Local Kafka and Kpow with Docker Compose

[![Release to DockerHub](https://github.com/operatr-io/kpow-docker/actions/workflows/release.yml/badge.svg?branch=main)](https://github.com/operatr-io/kpow-docker/actions/workflows/release.yml)
![Docker Pulls](https://img.shields.io/docker/pulls/operatr/kpow)

### Versions

| Kpow Version                 | Confluent Container Version   | Kafka Equivalent                |
|------------------------------|-------------------------------|---------------------------------|
| `factorhouse/kpow-ce:latest` | `confluentinc/cp-kafka:7.5.3` | `org.apache.kafka/kafka:3.5.2`  |

## Introduction

This repository contains a Docker Compose environment that will start:

- A 3-node Kafka cluster
- Kafka Connect 
- Schema Registry 
- Kpow Community Edition or Kpow Commercial Trial (supports authentication, RBAC, etc)

All container images used support `linux/amd64` and `linux/arm64` platforms.

See [kafka-local](https://github.com/factorhouse/kafka-local) for a simple local configuration consisting of only Kafka.

## Prerequisites

### Install Docker

The local cluster runs with Docker Compose, so you will need to [install Docker](https://www.docker.com/).

Once Docker is installed, clone this repository and run the following commands from the base path.

### Clone this repository

```
git clone git@github.com:factorhouse/kpow-local.git
```

### Change into the repository directory

```
cd kpow-local
```

## Run Kafka resources with Kpow Community

### Add your license details to local-community.env

* Get a [free Kpow Community license](https://factorhouse.io/kpow/community/)
* Enter the license details into [resoources/kpow/local-community.env](resources/kpow/local-community.env)

```
BOOTSTRAP=kafka-1:19092,kafka-2:19093,kafka-3:19094
CONNECT_REST_URL=http://connect:8083
SCHEMA_REGISTRY_URL=http://schema:8081
SCHEMA_REGISTRY_AUTH=USER_INFO
SCHEMA_REGISTRY_USER=admin
SCHEMA_REGISTRY_PASSWORD=admin

### Your License Details
LICENSE_ID=<license-id>
LICENSE_CODE=<license-code>
LICENSEE=<licensee>
LICENSE_EXPIRY=<license-expiry>
LICENSE_SIGNATURE=<license-signature>
```

### Start docker-compose

```
❯ docker compose -f docker-compose-community.yml up
[+] Running 13/13
 ✔ kpow Pulled                                                                                                                                                                                                                                            2.7s
 ✔ schema 11 layers [⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿]      0B/0B      Pulled
 ...
 ...
```
**Note:** Kpow's UI will start once Kafka resources are available.

## Coordinates

* Kpow will be available at `http://localhost:3000`
* Kafka Connect will be available at `http://localhost:8083` (unauthenticated)
* Schema Registry will be available at `http://localhost:8001` (basic auth username is `admin` and password is `admin`)
* The Kafka brokers are accessible with bootstrap URL `127.0.0.1:9092,127.0.0.1:9093,127.0.0.1:9094` (unauthenticated)

## Extending the environment

### Custom Connectors

To add custom Kafka Connect connectors create a `connect` directory and add all JARs there.

For example, to add the [Debezium PostgresSQL connectors](https://debezium.io/documentation/reference/stable/connectors/postgresql.html):

```bash
mkdir -p kpow-local/connect
cd kpow-local/connect
curl -L -o debezium-connector-postgres-1.9.6.Final-plugin.tar.gz https://repo1.maven.org/maven2/io/debezium/debezium-connector-postgres/1.9.6.Final/debezium-connector-postgres-1.9.6.Final-plugin.tar.gz 
tar –xvzf debezium-connector-postgres-1.9.6.Final-plugin.tar.gz
```

## Support

Any issues? Contact [support](https://kpow.io/support) or view our [docs](https://docs.kpow.io).

## Kpow

![Kpow in action.](resources/kpow-ui.png)

## License

Copyright © Factor House 2021-2022.
