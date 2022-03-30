
# About iTunes-API

  

## Features
* play/stop/pause/playpause/next/previous control over what's playing.
* query to return what's currently playing.
* fetch the art of the currently playing song.
* set a specific playlist to play, by name.
* query to return a list of available AirPlay endpoints.
* set an AirPlay endpoint to be active. (This can be multiple, since iTunes supports it).



### Forever
iTunes API has support for [Forever](https://github.com/foreverjs/forever). It uses `launchd` on OS X to kick it off so that it starts on boot. There is no `init.d` support

### Network
Port: `8181`

  


## Logging
Production Logs: `logs/logs.log`
Development Logs: `stdout`



  

# Resources
*Here's a list of resources that may be returned in a response.*

  

#### NowPlaying Resource
The NowPlaying resource returns all the information about if iTunes is playing and what is playing.

  

```json

{
	"player_state": "playing",
	"volume": 60,
	"muted": false,
	"id": "AC4FFD2271422B47",
	"name": "Forever",
	"artist": "HAIM",
	"album": "Days Are Gone (2013)",
	"playlist": "Summer Jams",
	"shuffle": "songs",
	"repeat": "all"
}

```

  

#### Playlist Resource

  

The Playlist resource returns all the information about a playlist in your library.

  

```json
{
	"id": "outkast-the-90s",
	"name": "Outkast: The '90s",
	"loved": true,
	"duration_in_seconds": 4544,
	"time": "1:15:44"
},
```

  

#### AirPlayDevice Resource
The AirPlayDevice resource returns all the information about an available AirPlay device on your network.

  


```json
{
	"id": "63-22-fa-1f-f5-d4",
	"name": "Living Room",
	"kind": "Apple TV",
	"active": true,
	"selected": true,
	"volume": 60,
	"supports_video": true,
	"supports_audio": true,
	"network_address": "63:22:fa:1f:f5:d4" 
},

```

  

#### Info

Use these endpoints to query the current state of iTunes:


    GET /now_playing => NowPlayingResource
    GET /artwork => JPEG Data (image/jpeg)

  

#### Player Control

Use these endpoints to control what's currently playing:

 

    PUT /playpause => NowPlayingResource
    PUT /stop => NowPlayingResource
    PUT /previous => NowPlayingResource
    PUT /next => NowPlayingResource
    PUT /play => NowPlayingResource
    PUT /pause => NowPlayingResource
    PUT /volume [level=20] => NowPlayingResource
    PUT /volume [muted=true] => NowPlayingResource
    PUT /shuffle [mode=songs] => NowPlayingResource
    PUT /shuffle [mode=off] => NowPlayingResource
    PUT /repeat [mode=all] => NowPlayingResource
    PUT /repeat [mode=off] => NowPlayingResource

  
  

#### Playlists

Use this endpoint to start a specific playlist:

  

    GET /playlists => {"playlists": [PlaylistResource, PlaylistResource, ...]}
    PUT /playlists/:id/play => NowPlayingResource

  

#### AirPlay Control

Use these endpoints to query and set AirPlay devices. You can set multiple AirPlay devices to be used at the same time:

  

    GET /airplay_devices => {"airplay_devices": [AirPlayDevice, AirPlayDevice, ...]}
    GET /airplay_devices/:id => AirPlayDevice
    PUT /airplay_devices/:id/on => AirPlayDevice
    PUT /airplay_devices/:id/off => AirPlayDevice
    PUT /volume [level=20] => AirPlayDevice

 
