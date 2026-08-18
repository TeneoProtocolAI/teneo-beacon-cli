# Teneo Beacon CLI

`teneo-beacon` is a lightweight headless daemon that runs a [Teneo](https://teneo.pro) Beacon node on any always-on Linux machine — a Raspberry Pi, a home server, a NAS. It keeps your Beacon earning around the clock without a desktop app.

## Install

```bash
curl -sSL https://github.com/TeneoProtocolAI/teneo-beacon-cli/releases/latest/download/install.sh | bash
```

Supported: `x86_64`, `arm64` (Raspberry Pi 3B+/4/5/Zero 2 W), `armv7` (Pi 2/3).

**Windows server or PC?** Install WSL2 first (`wsl --install` in an admin PowerShell, then reboot), open the Ubuntu terminal, and run the same command there — everything below works identically inside WSL.

## Pair it with your account

```bash
teneo-beacon
```

A QR code and a link appear in the terminal. Scan the QR with your phone (or open the link) while logged in at [hub.teneo.pro](https://hub.teneo.pro), and confirm. That's it — the device registers itself and starts earning.

## Run it as a service (recommended)

```bash
sudo teneo-beacon --install-service
```

Starts on boot, restarts on failure, survives network and service outages on its own. Logs: `journalctl -u teneo-beacon -f`

## Good to know

- **Home connections earn the full rate.** Since v0.5.0, some datacenter/server IPs are also accepted on a separate reduced tier: they earn Beacon fragments at a **flat 50% rate, no points, and no referral bonuses**. VPN IPs and flagged hosting providers are not accepted. A home connection is always the better place to run a Beacon.
- **Update:** re-run the install one-liner, then `sudo systemctl restart teneo-beacon`.
- **Uninstall:** `sudo teneo-beacon --uninstall-service && sudo rm /usr/local/bin/teneo-beacon && rm -rf ~/.teneo-beacon`
- If the device ever needs re-pairing (e.g. after a long offline stretch), it prints a fresh pairing link in its logs and keeps running — nothing breaks.

This repository hosts release artifacts. For product information see [teneo.pro](https://teneo.pro).
