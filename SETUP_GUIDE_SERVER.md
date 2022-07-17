# setup guide
Este arquivo possui tudo necessário para conseguir levantar o(s) server(s) para rodarem *la catalog*.  

# containers
```yaml
services:
    mongo:
        container_name: mongo
        image: mongo
        ports:
            - "27017:27017"
        environment:
            MONGO_INITDB_ROOT_USERNAME: username
            MONGO_INITDB_ROOT_PASSWORD: password
        volumes:
            - ~/docker_vol/mongo:/data/db
    postgres:
        container_name: postgres
        image: postgres
        ports:
            - "5432:5432"
        environment:
            POSTGRES_USER: username
            POSTGRES_PASSWORD: password
        volumes:
            - ~/docker_vol/postgres:/var/lib/postgresql/data
    meilisearch:
        container_name: meilisearch
        image: getmeili/meilisearch
        ports:
            - "7700:7700"
        environment:
            MEILI_MASTER_KEY: password
        volumes:
            - ~/docker_vol/meilisearch:/data.ms
    rabbit:
        container_name: rabbit
        image: rabbitmq:3-management
        hostname: "rabbit"
        ports:
            - "5672:5672"
            - "15672:15672"
        environment:
            RABBITMQ_DEFAULT_USER: username
            RABBITMQ_DEFAULT_PASS: password
            RABBITMQ_DEFAULT_VHOST: "/"
        volumes:
            - ~/docker_vol/rabbit:/var/lib/rabbitmq
    redis:
        container_name: redis
        image: redis
        ports:
            - "6379:6379"
        volumes:
            - ~/docker_vol/redis:/data
    influx:
        container_name: influx
        image: influxdb
        ports:
            - "8086:8086"
        environment:
            DOCKER_INFLUXDB_INIT_USERNAME: username
            DOCKER_INFLUXDB_INIT_PASSWORD: password
            DOCKER_INFLUXDB_INIT_ORG: fake_org
            DOCKER_INFLUXDB_INIT_BUCKET: first_bucket
        volumes:
            - ~/docker_vol/influx:/var/lib/influxdb2
    metabase:
        container_name: metabase
        image: metabase/metabase
        ports:
            - "3000:3000"
        volumes:
            - ~/docker_vol/metabase:/metabase-data
```

# runners

```bash
cd ~/Documents
mkdir actions-runner && cd actions-runner
curl -o actions-runner-linux-x64-2.294.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.294.0/actions-runner-linux-x64-2.294.0.tar.gz
echo "a19a09f4eda5716e5d48ba86b6b78fc014880c5619b9dba4a059eaf65e131780  actions-runner-linux-x64-2.294.0.tar.gz" | shasum -a 256 -c
tar xzf ./actions-runner-linux-x64-2.294.0.tar.gz
./config.sh --url https://github.com/la-catalog --token ACHLNPVCFIFVUKTI3AS5PSLC2OHWC
./run.sh
```
