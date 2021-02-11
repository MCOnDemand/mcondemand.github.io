# Server Monitor

**Layer**: The server monitor is part of the *server* layer (layer 2) of the MCOD server architecture.

**Concept**: The Server Monitor makes sure servers are healthy.

## Server Statuses

- **Healthy** -- When a server is *healthy*, the MCOD daemon and the Minecraft server should both respond to pings.
- **Starting** -- When a server is *starting*, the MCOD daemon should respond to pings with a "starting" status. The Minecraft server should not yet respond to pings; however, its stdout/stderr may be accessible via the daemon.
- **Stopping** -- When a server is *stopping*, the MCOD dameon should respond to pings with a "stopping" status. The Minecraft server should not respond to pings; however, its stdout/stderr may be accessible via the daemon.
- **Restarting/reloading** -- When a server is *restarting*, the MCOD daemon should respond to pings with a "restarting/reloading" status. The Minecraft server should not respond, &c.
- **Unhealthy** -- Any time when the daemon does not respond, a server should be considered *unhealthy*. If the daemon responds as healthy, but the Minecraft server does not respond to a ping, the server should be considered *unhealthy*.
- **Dead** -- A server should be considered dead after it has been marked as *unhealthy* on 3-5 consecutive checks.

## Health checking

Server Monitors will periodically check the status of servers.
To handle the potential for many Server Monitors, all monitors will share a list of server statuses.

## Shared Statuses

In order to facilitate multiple Server Monitors, server statuses will be stored in a shared location.

The current working plan is to use a Sorted-set on the redis server.
The UNIX time of the last update on a status will be used as the "score" for items in the set.

*More research and planning to come.*
