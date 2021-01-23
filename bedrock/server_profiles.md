# Server Profiles

Information for how server instances should be configured will be stored in server profiles.

Server profiles will serve two jobs:

1. Store core configuration information. This includes: the server JAR to be used, links to the file objects necessary to run the server. In the future, this may include: list of associated mods or plugins, links to plugin and mod configuration files.
2. Store file-based configuration. This includes: server.properties, spigot.conf, bukkit.conf, plugin/mod JARs, plugin/mod configs.

For the first iteration of server profiles, the file portion of a server profile will contain all files necessary to run a server except the JAR and the world files.
The JAR file will be downloaded based on the profile.
The world files will be downloaded seperately. (See [World Storage](/world_storage.md))
