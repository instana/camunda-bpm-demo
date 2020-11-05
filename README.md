# Camunda with configuration-based Java Trace SDK

## Configure

Create a `.env` file in the root of the checked-out version of this repository and enter the following text, with the values adjusted as necessary:

```text
agent_key=<TODO FILL UP>
agent_endpoint=<local ip or remote host; e.g., saas-us-west-2.instana.io>
agent_endpoint_port=<443 already set as default; or 4443 for local>
agent_zone=<name of the zone for the agent; default: otel-demo>
```

## Launch

```sh
docker-compose up
```

Then, open your browser and go to `http://localhost:8080/camunda-welcome/index.html` to open Camunda.

## Instana configurations

The instrumentation is specified in the [agent/configuration.yaml](agent/configuration.yaml) file.

Changes to the configuration are hot-reloaded by the agent, but the application needs to restart in order to apply a new version.

## See it in action

1. Go to
   [Camuda Tasklist](http://localhost:8080/camunda/app/tasklist/default/#/login)
1. Login with `demo/demo`
1. Assign reviewer `demo` of one of the two tasks
1. Check in Instana UI that new trace is created
   - `service.name`: `camunda-bpm-platform`
   - `call.type`: `BATCH`
