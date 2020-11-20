# [kPow for Apache Kafka®](https://kpow.io) 
## Evaluate locally with Docker Compose

### To run kPow locally against a Dockerized 3-node Apache Kafka® cluster:

kPow will run with any Kafka Cluster from v1.0+. 

See our [User Guide](https://docs.kpow.io) for full documentation, this is one simple configuration:

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
docker run --network=kpow_default -p 3000:3000 --env-file ./local.env operatr/kpow:latest
```

7. **VIEW** kPow on http://localhost:3000. kPow takes **two minutes** to initialize state on startup.

8. **NOTE** The Kafka brokers are accessible on localhost:9092/9093/9094 if you want to configure other services.
-----

Any issues? Just [raise a ticket](https://github.com/operatr-io/community/issues).

Copyright © Operatr.IO 2020.
