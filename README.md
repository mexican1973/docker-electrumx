
# docker-electrumx

[![Build Status](https://travis-ci.org/lukechilds/docker-electrumx.svg?branch=master)](https://travis-ci.org/lukechilds/docker-electrumx)
[![Image Layers](https://images.microbadger.com/badges/image/lukechilds/electrumx.svg)](https://microbadger.com/images/lukechilds/electrumx)
[![Docker Pulls](https://img.shields.io/docker/pulls/lukechilds/electrumx.svg)](https://hub.docker.com/r/lukechilds/electrumx/)

> Run an Electrum server with one command

An easily configurable Docker image for running an Electrum server.

## Usage

```
docker run \
  -v /home/zcluser/zcl_electrum_db:/data \
  -e DAEMON_URL=http://ZCLuser:ZCLpass@localhost:8023 \
  -e COIN=Zclassic \
  -p 50002:50002 \
  -e SSL_PORT=50002 \
  -e HOST=0.0.0.0 \
  -e RPC_PORT=8023 \
  -e RPC_HOST=0.0.0.0 \
  -e PEER_DISCOVERY=On \
  -e MAX_SESSIONS=2000 \
  -e BANDWIDTH_LIMIT=10000000 \
  -e SSL_KEYFILE=/home/zcluser/server.key \
  -e SSL_CERTFILE=/home/zcluser/server.crt \
  -e DB_DIRECTORY=/home/zcluser/zcl_electrum_db \
  zclassicdev/electrumx:latest
```

If there's an SSL certificate/key (`electrumx.crt`/`electrumx.key`) in the `/data` volume it'll be used. If not, one will be generated for you.

You can view all ElectrumX environment variables here: https://github.com/ZclassicDev/electrumx/blob/master/docs/environment.rst

### TCP Port

By default only the SSL port is exposed. You can expose the unencrypted TCP port with `-p 50001:50001`, although this is strongly discouraged.


## License

MIT © Luke Childs
