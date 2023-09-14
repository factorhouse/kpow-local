# [Kpow for Apache Kafka®](https://kpow.io)
[![Release to DockerHub](https://github.com/operatr-io/kpow-docker/actions/workflows/release.yml/badge.svg?branch=main)](https://github.com/operatr-io/kpow-docker/actions/workflows/release.yml)
![Docker Pulls](https://img.shields.io/docker/pulls/operatr/operatr)

## Local Development with Kpow

This repository contains a Docker Compose environment that will start:

- A 3-node Kafka cluster
- Kafka Connect 
- Schema Registry 
- Kpow Community Edition

Perfect for local development!

All container images used support `linux/amd64` and `linux/arm64` platforms.

## Usage

### Clone this repo

```
git clone git@github.com:factorhouse/kpow-local.git
```

### Change into the repo directory

```
cd kpow-local
```

### Add your license details to local.env

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
docker compose up
```
**Note:** Kpow's UI will start once Kafka Connect becomes healthy.

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
