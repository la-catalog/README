# setup server
Este arquivo possui tudo necessário para conseguir levantar o server da organização localmente ou em uma máquina externa.  

**Atenção**: [Fazer a instalação como dev primeiro](./INSTALL_DEV.md)  
**Recomendação**: [Copiar a chave para o server](https://askubuntu.com/questions/4830/easiest-way-to-copy-ssh-keys-to-another-machine)  

# docker-compose
```yaml
services:
    mongo:
        container_name: mongo
        image: mongo
        ports:
            - "27017:27017"
        environment:
            MONGO_INITDB_ROOT_USERNAME: ${MONGO_USER}
            MONGO_INITDB_ROOT_PASSWORD: ${MONGO_PASS}
    postgres:
        container_name: postgres
        image: postgres
        ports:
            - "5432:5432"
        environment:
            POSTGRES_USER: ${POSTGRES_USER}
            POSTGRES_PASSWORD: ${POSTGRES_PASS}
    meili:
        container_name: meili
        image: getmeili/meilisearch
        ports:
            - "7700:7700"
        environment:
            MEILI_MASTER_KEY: ${MEILI_KEY}
    rabbit:
        container_name: rabbit
        image: rabbitmq:3-management
        hostname: "rabbit"
        ports:
            - "5672:5672"
            - "15672:15672"
        environment:
            RABBITMQ_DEFAULT_USER: ${RABBIT_USER}
            RABBITMQ_DEFAULT_PASS: ${RABBIT_PASS}
            RABBITMQ_DEFAULT_VHOST: "/"
    redis:
        container_name: redis
        image: redis
        ports:
            - "6379:6379"
    influx:
        container_name: influx
        image: influxdb
        ports:
            - "8086:8086"
        environment:
            DOCKER_INFLUXDB_INIT_USERNAME: ${INFLUX_USER}
            DOCKER_INFLUXDB_INIT_PASSWORD: ${INFLUX_PASS}
            DOCKER_INFLUXDB_INIT_ORG: la-catalog
            DOCKER_INFLUXDB_INIT_BUCKET: la-catalog
```

```yaml
# TODO: not remove data when the container stop
    vault:
        container_name: vault
        image: vault
        ports:
            - "8200:8200"
        environment:
            VAULT_DEV_ROOT_TOKEN_ID: ${VAULT_TOKEN}
            VAULT_DEV_LISTEN_ADDRESS: 0.0.0.0:8200
```
