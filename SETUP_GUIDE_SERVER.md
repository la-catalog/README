# setup guide
Este arquivo possui tudo necessário para conseguir levantar o(s) server(s) para rodarem *la catalog*.  
**Observação**: Como a organização em si é só uma experiência, esses setings podem não ser os melhores atualmente (nem os mais seguros)  

# runner
Na raiz da organização crie um runner para executar as actions.  
O token para criação não é válido para sempre.  

# docker-compose
```yaml
services:
    mongo:
        container_name: mongo
        image: mongo
        ports:
            - "27017:27017"
        environment:
            MONGO_INITDB_ROOT_USERNAME: lacatalog
            MONGO_INITDB_ROOT_PASSWORD: lamongo
        volumes:
            - ~/docker_vol/mongo:/data/db
    postgres:
        container_name: postgres
        image: postgres
        ports:
            - "5432:5432"
        environment:
            POSTGRES_USER: lacatalog
            POSTGRES_PASSWORD: lapostgres
        volumes:
            - ~/docker_vol/postgres:/var/lib/postgresql/data
    meili:
        container_name: meilisearch
        image: getmeili/meilisearch
        ports:
            - "7700:7700"
        environment:
            MEILI_MASTER_KEY: lameili
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
            RABBITMQ_DEFAULT_USER: lacatalog
            RABBITMQ_DEFAULT_PASS: larabbit
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
            DOCKER_INFLUXDB_INIT_USERNAME: lacatalog
            DOCKER_INFLUXDB_INIT_PASSWORD: lainflux
            DOCKER_INFLUXDB_INIT_ORG: la-catalog
            DOCKER_INFLUXDB_INIT_BUCKET: la-catalog
        volumes:
            - ~/docker_vol/influx:/var/lib/influxdb2
```
