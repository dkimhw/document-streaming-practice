## Setup

### Run `pip`

```python
pip install -r ./api-ingest/requirements.txt
```

### Start Kafka

```docker
docker-compose -f docker-compose-kafka.yml up
```

### Create Topics

- Access container via terminal
- `cd /opt/bitnami/kafka/bin`
- `./kafka-topics.sh --create --topic ingestion-topic --bootstrap-server localhost:9092`
- `./kafka-topics.sh --create --topic spark-output --bootstrap-server localhost:9092`
- Check that topics were installed: `./kafka-topics.sh --list --bootstrap-server localhost:9092`

### Deploy API

- Run:

```docker
docker build -t api-ingest .
```

- Check that image called `api-ingest` exists:

```docker
docker images
```

- ## Start up docker

```docker
docker run --rm --network <network_name> --name my-api-ingest -p 80:80 api-ingest

docker run --rm --network document-streaming-practice_default --name my-api-ingest -p 80:80 api-ingest
```
