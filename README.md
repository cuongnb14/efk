# EFK

![Architecture](https://raw.githubusercontent.com/cuongnb14/efk/master/efk-architecture.png)

## Setup EFK Center
```
docker-comnpose up -d
```

## Run docker container with fluentd log driver
with docker run
```
docker run httpd:2.2.32 -p 80:80 \
--log-driver=fluentd \
--log-opt fluentd-address=$FLUENTD_HOST:24224 \
--log-opt tag=evano.drive \
```

with docker compose
```
version: '2'
services:
  web:
    image: httpd:2.2.32
    ports:
      - "85:80"
    logging:
      driver: "fluentd"
      options:
        fluentd-address: localhost:24224
        tag: httpd.access
```