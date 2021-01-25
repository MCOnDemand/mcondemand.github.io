# MCOD Bedrock

This document is focused **Bedrock**, the system which is the foundation of all MCOD services.

## Server system layers

The server system has a number of different layers.

1. **Network level** -
This level is concerned with networking issues.
This will include a dynamic DNS system as well as security features.
2. **Instance level** -
This level is only concerned with the actual machines servers are spawned on.
At the moment, this means DO droplets.
In the future this may be k8s pods.
3. **Server level** -
This level is concerned with the services running on an instance.
These services include the Minecraft server and the MCOD daemon.

## Concept Outline

**Concept**: Bedrock is a system for automatically deploying and managing ephemeral Minecraft servers.

**Statement of Need**: Users need to be able to start properly configured Minecraft servers in minutes.

### Components

**Component 1**: [Server Management](/server_mgmt.md)

- Spawn servers
- Monitor server health
- Destroy "dead" servers

**Component 2**: [Server Profiles](/server_profiles.md)

- Store core configuration data
- Store configuration files such that they can be easily edited, uploaded, and downloaded.
- Transfer all configuration data to servers quickly.

**Component 3**: [World Storage](/world_storage.md)

- Provide long-term storage for worlds
- Minimize bandwidth usage
- Maintain change history

**Component 4**: Network Management

- Provide a secure network system
- Allow dynamic DNS assignment
- Monitor network traffic

**Component 5**: Logging

- Aggregate server logs
- Provide a way of searching logs
