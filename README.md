# Mattermost WebRTC

This is a repository to generate a Vagrant machine or a docker image to use the WebRTC functionality in Mattermost


## Mattermost WebRTC Vagrant machine

### Requirements
- Vagrant
- Virtualbox

TODO: Create a functional vagrant machine

## Mattermost WebRTC Docker Preview Image

This is a single-machine Docker image for previewing the Mattermost WebRTC features.

### Usage

Please see [documentation for usage](https://docs.mattermost.com/deployment/webrtc.html). 

If you have Docker already set up, you can run this image in one line: 

```
docker run --name mattermost-webrtc -p 7088:7088 -p 7089:7089 -p 8188:8188 -p 8189:8189 -d mattermost/webrtc:latest
```

### Configuring Mattermost WebRTC

In Mattermost System Console -> Integrations -> **WebRTC (Beta)** and set the following:

- Enable Mattermost WebRTC: **true**
- Gateway Websocket URL: **wss://dockerhost:8189**
- Gateway Admin URL: **https://dockerhost:7089/admin**
- Gateway Admin Secret: **janusoverlord**
- Leave Blank **STUN URI**, **TURN URI**, **TURN Username** and **TURN Shared Key** unless you configure have [Coturn](https://github.com/coturn/coturn/wiki) configured.

Because the WebRTC docker image uses a self-signed certificate you need to enable the ability to make
requests from Mattermost to external services using insecure connections.

In Mattermost System Console -> Security -> **Connections**
- Enable Insecure Outgoing Connections: true