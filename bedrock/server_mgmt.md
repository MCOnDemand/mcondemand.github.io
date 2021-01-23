# Server Management Component

This component manages the lifecycle of server instances.

### Instance Lifecycle

1. Server instance is spawned
2. Instances are pinged to monitor their status
3. Instances are destroyed when deemed "dead"

Is that the best way to handle server lifecycle?
I need to consider different cases.

What happens when a server is live, but pings fail?
What happens when a server is in the process of shutting down?
How are shutdown messages sent to the instance from other sources (i.e. Website, CLI, API)?
