# drone-convert-starlark

A conversion plugin that provides optional support for generating pipeline configuration files via Starlark scripting. _Please note this project requires Drone server version 1.4 or higher._

Questions and Support:<br/>
https://discourse.drone.io

Bug Tracker:<br/>
https://discourse.drone.io/c/bugs

Features and Roadmap:<br/>
https://trello.com/b/ttae5E5o/drone

## Installation

Create a shared secret:

```text
$ openssl rand -hex 16
bea26a2221fd8090ea38720fc445eca6
```

Download and run the plugin:

```text
$ docker run -d \
  --publish=3000:3000 \
  --env=DRONE_DEBUG=true \
  --env=DRONE_SECRET=bea26a2221fd8090ea38720fc445eca6 \
  --restart=always \
  --name=starlark drone/drone-convert-starlark
```

Update your Drone server configuration to include the plugin address and the shared secret.

```text
DRONE_CONVERT_PLUGIN_ENDPOINT=http://1.2.3.4:3000
DRONE_CONVERT_PLUGIN_SECRET=bea26a2221fd8090ea38720fc445eca6
```

## Testing

You can test the extension using the command line utility. Provide the command line utility with the conversion extension endpoint and secret.

```text
$ export DRONE_CONVERT_ENDPOINT=http://1.2.3.4:3000
$ export DRONE_CONVERT_SECRET=bea26a2221fd8090ea38720fc445eca6
```

Use the command line utility to convert the Starlar script:

```
$ drone plugins convert path/to/.drone.star
```
