# Media Stack

## Plex
Deploy the docker compose file, then head to *<Your Server's IP Address>*:32400/web to configure Plex.

### [PlexTraktSync](https://github.com/Taxel/PlexTraktSync)

Instead of using the standard [docker compose up -d] to push, use:

```docker
docker compose run --rm plextraktsync sync
```
Be sure to have created your Trakt API app already, you'll need:
* Your Plex email
* Your Plex password
* Client ID for your Trakt App
* Client Secret for your Trakt App. 

All of that goes on in your CLI

Use the code you get to [Activate your Device](https://github.com/Taxel/PlexTraktSync)

### Tautulli

### Kometa

## Arrs
### Bazarr
### Sonarr
### Prowlarr
### Radarr
### Huntarr