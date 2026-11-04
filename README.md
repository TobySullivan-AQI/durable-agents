# durable-agents

An APM package of durable-agent identity and persistence instructions.

From the root of your repository, initialize APM if you do not already have an `apm.yml`:

```sh
apm init
```

Add and install the package, then compile the instructions for your agent:

```sh
apm install TobySullivan-AQI/durable-agents
apm compile
```

The install command adds the package to your `apm.yml`. In an existing checkout where the dependency is already declared, run `apm install` to restore it before `apm compile`.
