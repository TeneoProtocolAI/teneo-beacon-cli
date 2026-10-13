# Teneo Beacon CLI

**Run a Teneo Beacon on any always-on machine: a Raspberry Pi, a home server, a NAS or a Mac mini.**

`teneo-beacon` is the headless edition of [Teneo Beacon](https://github.com/TeneoProtocolAI/teneo-node-app-release-beta). It's a single self-contained binary with no desktop and no dependencies. It runs 24/7, pairs to your Teneo account with a QR code, and earns Fragments and Teneo Points around the clock.

Beacon operators form a global network of real residential connections that gives AI agents live access to the open web, with **20,000+ verified operators in 150+ countries**. A device that is always on is one of the most valuable things you can add to it.

**Latest: [cli-v0.6.0](https://github.com/TeneoProtocolAI/teneo-beacon-cli/releases/latest)**

## Supported platforms

| Platform | Binary |
|----------|--------|
| Linux x86_64 | `teneo-beacon-x86_64` |
| Linux arm64: Raspberry Pi 3B+ / 4 / 5 / Zero 2 W, ARM servers | `teneo-beacon-arm64` |
| Linux armv7: Raspberry Pi 2 / 3 (32-bit OS) | `teneo-beacon-armv7` |
| macOS (Apple Silicon + Intel, universal) | `teneo-beacon-macos` |
| Windows | Run the Linux build inside WSL2 (see below) |

## Install

```bash
curl -sSL https://github.com/TeneoProtocolAI/teneo-beacon-cli/releases/latest/download/install.sh | bash
```

The installer detects your platform, downloads the matching binary from this repository's latest release and installs it to `/usr/local/bin/teneo-beacon`. You can also download a binary from [Releases](https://github.com/TeneoProtocolAI/teneo-beacon-cli/releases) and install it yourself.

**Windows:** install WSL2 (`wsl --install` in an administrator PowerShell, then reboot), open the Ubuntu terminal and run the same command.

## Pair with your account

```bash
teneo-beacon
```

A QR code and a link appear in the terminal. Open the link (or scan the QR with your phone) while signed in at [hub.teneo.pro](https://hub.teneo.pro) and confirm. The device registers itself and starts earning.

## Run as a service (recommended)

```bash
sudo teneo-beacon --install-service   # Linux (systemd): starts on boot
teneo-beacon --install-service        # macOS (launchd): starts at login, no sudo
```

The service restarts automatically and recovers from network outages without your help. If it ever needs to be paired again, it writes a fresh pairing link to its log and keeps running.

| | Linux | macOS |
|---|---|---|
| Logs | `journalctl -u teneo-beacon -f` | `~/Library/Logs/teneo-beacon.log` |
| Update | Re-run the install command, then `sudo systemctl restart teneo-beacon` | Re-run the install command, then `teneo-beacon --install-service` |
| Uninstall | `sudo teneo-beacon --uninstall-service && sudo rm /usr/local/bin/teneo-beacon && rm -rf ~/.teneo-beacon` | `teneo-beacon --uninstall-service && sudo rm /usr/local/bin/teneo-beacon && rm -rf ~/.teneo-beacon` |

Other options: `teneo-beacon --help`.

## Where to run it

- **Home and mobile connections are what Beacon is built for.** A Pi or home server behind your router is ideal.
- **Servers and VPS:** hosting connections are handled under separate rules. They may earn at a reduced rate or may not be accepted.
- **VPNs and proxies are not supported.**

## Safety

- Beacon relays network connections only. It never touches your files or other software.
- It refuses connections to your local network, your router and other private addresses.
- Email sending, remote login, DNS, file sharing, databases and device-debugging ports are blocked on the device itself.
- Participation is opt-in and tied to your Teneo account. Stop the service and the device stops sharing.

See the [Terms of Service](https://legal.teneo.pro/terms) and [Privacy Policy](https://legal.teneo.pro/privacy).

## Links

[teneo.pro](https://teneo.pro) · [Expedition Hub](https://hub.teneo.pro) · [Desktop & mobile apps](https://github.com/TeneoProtocolAI/teneo-node-app-release-beta) · [Discord](https://discord.gg/WJQpSUsbu3) · [X](https://x.com/teneo_protocol)

This repository hosts the official `teneo-beacon` release binaries and installer.
