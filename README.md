# Original Torrent — Farcaster MiniApp Audio Streamer

Original Torrent is a browser-only torrent streamer for music creators and listeners. It uses WebTorrent over WebRTC so both creators and early listeners can distribute audio peer-to-peer without any servers. The app is designed to run as a Farcaster MiniApp and deploy easily to static hosting.

## Features
- **Farcaster MiniApp ready** – includes `/.well-known/farcaster.json` manifest and frame tags.
- **WebRTC + WebTorrent** – pure browser streaming over WebSocket trackers (no TCP/UDP, no server).
- **Listener mode** – paste a magnet URI to stream audio into a native `<audio>` player.
- **Creator mode** – select a local audio file, generate a magnet link, and seed directly from the browser.
- **Minimal UI** – plain HTML + JS, no build step or framework.
- **Runtime config** – trackers and ICE servers are stored in `config.json` for easy updates.
- **Logging & stats** – live peer count, speed, and progress display.

## Getting Started
1. Clone the repository.
2. Open `index.html` in a modern browser.

No installation or build step is required. The app seeds or streams audio directly from the browser.

## Configuration
Edit `config.json` to change the list of WebTorrent trackers, WebRTC ICE servers, or the number of bytes to prefetch before playback.

## Development
This project intentionally avoids build tools and external dependencies. Keep contributions self-contained and minimal. Run `npm test` if test scripts are added in the future.

