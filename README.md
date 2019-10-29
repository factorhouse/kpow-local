# [OPERATR](https://operatr.io) with Docker Compose

### Run OPERATR locally against a Dockerized 3-node Apache Kafka® cluster.

To connect OPERATR (or other streaming services) to Kafka running with docker-compose we need to ensure they are on the same network. OPERATR will run against any Kafka Cluster with minimum 3 nodes. This is one example setup:

## Instructions

1. **CLONE** this repository.

2. **EDIT** local.env and replace YOUR_CODE_HERE with your trial code. Need a code? [Get one now](https://operatr.io/#/get-operatr).

3. **START** a new 3-node containerized Kafka cluster with a network named 'operatr_default'

```bash
docker-compose -p operatr up
```

4. **START** OPERATR with the same Docker network and the correct local environment settings.

```bash
docker run --network=operatr_default -p 3000:3000 --env-file ./local.env operatr/operatr:latest
```

5. **VIEW** OPERATR on localhost:3000. Graphs and data should be populated within 2 minutes.

-----

Any issues? Just [raise a ticket](https://github.com/operatr-io/community/issues).

Copyright © OPERATR IO, Inc. 2019. 
