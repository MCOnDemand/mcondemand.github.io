# MCOD Bedrock

This document is focused **Bedrock**, the system which is the foundation of all MCOD services.

## Concept Outline

__**Concept**__: Bedrock is a system for automatically deploying and managing ephemeral Minecraft servers.

__**Statement of Need**__: Users need to be able to start properly configured Minecraft servers in minutes.

### Components

__**Component 1**: Server Management__

- Spawn servers
- Monitor server health
- Destroy "dead" servers

__**Component 2**: Server Profiles__

- Store core configuration data
- Store configuration files such that they can be easily edited, uploaded, and downloaded.
- Transfer all configuration data to servers quickly.

__**Component 3**: World Storage__

- Provide long-term storage for worlds
- Minimize bandwidth usage
- Maintain change history

__**Component 4**: Network Management__

- Provide a secure network system
- Allow dynamic DNS assignment
- Monitor network traffic

__**Component 5**: Logging__

- Aggregate server logs
- Provide a way of searching logs
