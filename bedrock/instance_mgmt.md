# Instance Manager

**Layer**: The Instance Manager is part of the *Instance Layer* of [Bedrock](/bedrock/).

**Concept**: The Instance Manager executes lifecycle processes of instances.

## Instance Lifecycle

The instance has three distinct stages in its lifecycle:

1. **Creation** - The instance is created. 
Startup data is loaded onto the instance via cloud-init.
2. **Runtime** - The instance is running.
3. **Destruction** - The instance is destroyed.
When possible, destruction should occur after graceful shutdown.
"Unhealthy" instances may be destroyed without graceful shutdown.

## Instance Manager Jobs

The instance manager will be responsible for two jobs:

1. Creating instances
2. Destroying instances

Currently there are no plans for the instance manager actually monitoring instances during runtime.
Monitoring will be done on the server level.

### Creating Instances

Instances will be created by making an HTTP request to the Instance Management service.

A request should looks something like:

```JSON
{
    "method": "POST",
    "body": "{...}"
}
```

The service will respond with `202 (Accepted)` for successful instance creation requests.

The service will respond with `4xx` and `5xx` codes for failed requests.

### Destroying Instances

There will be no HTTP request to destroy an instance. (Except for testing.)

When an instance should be destroyed, its identifier (which I have yet to choose) will be added a list of instances marked for destruction.
The Instance Manager will regularly check this list, and destroy any instances which it finds.
