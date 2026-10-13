# UDPNetworking

A lightweight C++ UDP networking library with **selective reliable messaging**, **custom data serialization**, and **snapshot interpolation**, built on SDL3.

![Demo screenshot or GIF](docs/demo.gif)

## Features
- **Generic data streaming**: define your own data types with custom serialize/deserialize methods; the library handles transport.
- **Optional reliability over UDP**: mark individual messages as important and they're acknowledged and resent. Everything else stays fire-and-forget.
- **Networked value interpolation**: toggle it in settings, with a configurable delay, to smooth remote objects on unstable connections.
- **Engine-agnostic core**: no engine dependencies in the core, so it can be wrapped for any engine or application (wrappers planned).


## Demo
Three windows run together: a **control GUI** (Dear ImGui) and **two client windows** (SDL3).

| Control | Action |
|---|---|
| `WASD` | Move your square |
| Mouse hover | Choose which client you're controlling |
| `M` | Send a reliable message from the selected client |

In the control GUI you can:
- adjust simulated **packet loss**
- toggle **interpolation** and set its **delay** per client

Each client shows your square (green), the remote player (yellow), and the reliable-message indicators.
Try 30% packet loss with interpolation off and then on to see the difference.

## Building
**Requirements:** CMake 3.x+, a C++17 compiler

```bash
git clone https://github.com/JonnyCollinsPlusPlus/UDPNetworking
cd UDPNetworking
cmake -B build
cmake --build build
./build/Debug/DemoApp   # DemoApp.exe on Windows
```
Tested on: Windows (MSVC).


## Status
**Working:** core networking is stable; the demo is fully functional.

**Limitations**
- Tested on localhost with simulated packet loss; not yet on a real LAN.
- No NAT traversal (out of scope).

## Roadmap
- [ ] LAN testing
- [ ] Unit tests and CI (GitHub Actions)
- [ ] API documentation
- [ ] Engine and framework wrappers (e.g. Godot, Unity)
- [ ] Cleanup and performance profiling
