# Original Torrent — Farcaster MiniApp Audio Streamer

Original Torrent is a browser-only torrent streamer for music creators and listeners. It uses WebTorrent over WebRTC so both creators and early listeners can distribute audio peer-to-peer without any servers. The app is designed to run as a Farcaster MiniApp and deploy easily to static hosting.

## Features
- **Farcaster MiniApp ready** – includes `/.well-known/farcaster.json` manifest and frame tags.
- **WebRTC + WebTorrent** – pure browser streaming over WebSocket trackers (no TCP/UDP, no server).
- **Listener mode** – paste a magnet URI to stream audio into a native `<audio>` player.
- **Combined trackers** – merges WebSocket trackers from the magnet URI with those in `config.json` and ignores unsupported protocols.
- **Creator mode** – select a local audio file, generate a magnet link, copy it, and seed directly from the browser.
- **Minimal UI** – plain HTML + JS, no build step or framework.
- **Runtime config** – trackers and ICE servers are stored in `config.json` for easy updates.
- **Graceful config errors** – displays a message if `config.json` fails to load or parse.
- **Logging & stats** – live peer count, speed, and progress display.
- **Light background** – explicitly sets a white background for consistent readability.

## Getting Started
1. Clone the repository.
2. Open `index.html` in a modern browser.

No installation or build step is required. The app seeds or streams audio directly from the browser.

## Configuration
Edit `config.json` to control connectivity and playback behavior. Both listening and seeding use these values.

### Options
- `iceServers`: WebRTC STUN/TURN servers. The default TURN entries use the public [OpenRelay](https://www.metered.ca/tools/openrelay/) service with `openrelayproject` credentials for testing. For production, obtain your own `username` and `credential` from a TURN provider.
- `trackers`: WebSocket trackers used for peer discovery.
- `prerollBytes`: Number of bytes to fetch before playback begins.
- `maxConns`: Maximum number of simultaneous peer connections.
- `strategy`: Piece download strategy for seeding (`sequential` streams from start; playback always uses sequential).
- `dht`: Enable distributed hash table peer discovery.
- `lsd`: Enable local service discovery on the LAN.
- `webSeeds`: Allow fetching pieces from HTTP/HTTPS web seeds.
- `uploadLimit`: Upload bandwidth limit in bytes per second (`-1` for unlimited).
- `downloadLimit`: Download bandwidth limit in bytes per second (`-1` for unlimited).
- `blocklist`: Array of IP addresses or ranges to block.

### TURN credentials
Obtain TURN credentials from a provider such as Twilio, Metered, or a self-hosted Coturn server. Avoid committing sensitive keys to version control; serve a custom `config.json` or inject the values at deploy time so they remain private.

## Development
This project intentionally avoids build tools and external dependencies. Keep contributions self-contained and minimal. Run `npm test` if test scripts are added in the future.

