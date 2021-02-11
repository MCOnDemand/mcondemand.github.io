# Server Profiles

**Concept**: Server Profiles are packages which contain all configuration information for a server.

## Configuration Types

Server profiles need to store two types of information:

1. Server configuration --
This is information related to how the server should be run:
What executable should be used?
2. Game configuration --
This is the collection of files which configures the game server, including:
server.properties, spigot/bukkit/paper/... configs, permissions, plugin/mod configs, plugins/mods, ...
Basically any file that is written to/read from the execution dir falls into this category.

## Server Profile Format

**Server config** will be stored as a *document in a document store*.

- Server config must be quickly and easily accessible for reads/writes
- Server config will have *mostly* defined structure

**Game config** will be stored as an *archive file in blob storage*.

- Game config should maintain the expected directory structure
- Game config should be relatively unchanging once first created
- Game config must support both text and binary data

*Would it make more sense to use the repository system from worlds for game config?*

## Server Profile Data Structure

While there are multiple components to a Server Profile, the core object is a document.
The current structure of this document is as follows:

```JSON
{
    "_id": UUID,
    "name": string,
    "owner": UUID,
    "config": {
        "jar": {
            "type": string,
            "version": string,
        },
        "player_lists": {
            "enable_whitelist": bool,
            "banned": [banned players],
            "allowed": [allowed players (when whitelist is enabled)],
        }
    },
    files: [
        {
            "url": string,
            "type": repository|file,
            "version": string,
            "name": string,
            "rules": [
                {
                }
            ]
        }
    ]
}
```

```JSON
{
    "_id": UUID,
    "name": string,
    "owner": UUID,
    "jar": {
        "flavor": string,
        "version": string,
    },
    "assets":{
        
    }
}
```

## Server Profile System
