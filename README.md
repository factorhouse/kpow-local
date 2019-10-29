# [OPERATR](https://operatr.io) with Docker Compose

Run OPERATR locally against a containerized 3-node Apache Kafka® cluster.

## Instructions

1. Clone this repository.

2. EDIT local.env and replace YOUR_CODE_HERE with your trial code.

3. START a new 3-node containerized Kafka cluster with a network named 'operatr_default'

```bash
docker-compose -p operatr up
```

4. START OPERATR with the same Docker network and the correct local environment settings.

```bash
docker run --network=operatr_default -p 3000:3000 --env-file ./local.env operatr/operatr:latest
```
