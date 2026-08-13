# Unraid Community Applications Templates

This repository contains XML templates for publishing and maintaining Unraid Community Applications (CA) entries.

## What Is In This Repo

- [ca_profile.xml](ca_profile.xml): Maintainer profile metadata used by CA.
- [hrhomerun.xml](hrhomerun.xml): Template for the HDHomeRun DVR container.
- [Spinmatch.xml](Spinmatch.xml): Template for the Spinmatch music library container.
- [kydns.xml](kydns.xml): Template for the KyDNS local DNS server container.

This repository is the single source of truth for both templates. Each one sets
its `TemplateURL` back to its raw URL here, so edits reach existing installs.

## Included Templates

### HDHomeRunDVR

- XML file: [hrhomerun.xml](hrhomerun.xml)
- Container repository: `ghcr.io/yoshiofthewire/docker-hdhomerundvr:latest`
- Network mode: host
- Typical usage: run SiliconDust HDHomeRun DVR engine with host networking for discovery
- Support thread: [Unraid forums](https://forums.unraid.net/topic/199378-support-hdhomerun-dvr-20250815/)

Main template fields in this file include:

- Required host path mapping for DVR recordings (`/hdhomerun`)
- Links to project and upstream README

Host networking is required for HDHomeRun device discovery (UDP broadcast on
65001); because of that no port mappings are declared, since Unraid ignores them
in host mode.

### Spinmatch

- XML file: [Spinmatch.xml](Spinmatch.xml)
- Container repository: `ghcr.io/yoshiofthewire/spinmatch:latest`
- Network mode: bridge, web UI on port 3000
- Typical usage: search MusicBrainz, verify YouTube links, and organize a local
  music library via acoustic fingerprinting
- Support thread: [GitHub issues](https://github.com/Yoshiofthewire/Spinmatch/issues)

Requires a MusicBrainz contact email. Ingest and library features additionally
need the Music and Ingest directory mappings; an AcoustID key is optional.

### KyDNS

- XML file: [kydns.xml](kydns.xml)
- Container repository: `ghcr.io/yoshiofthewire/kydns-server:latest`
- Network mode: custom `br0`, with its own LAN address
- Typical usage: local DNS and service directory for a homelab, resolving
  private names on `home.arpa` and forwarding the rest over DNS-over-TLS
- Support thread: [GitHub issues](https://github.com/Yoshiofthewire/kydns-server/issues)

KyDNS takes its own LAN address so it owns port 53 there, rather than fighting
the Unraid host or an existing AdGuard Home / Pi-hole. The fixed IP must sit
inside the `br0` subnet and outside the router's DHCP pool.

The icon is [kydns-icon.png](kydns-icon.png), rendered at 512x512 from
[kydns-icon.svg](kydns-icon.svg) with `rsvg-convert`. It is the same mark as
the app's favicon; re-render rather than editing the PNG.

No config file is needed for a first install — the image ships a working one
with `data_dir: /var/lib/kydns` and `admin.listen: "0.0.0.0:8053"`. The Config
File mapping is optional and hidden under Advanced, for settings the template
does not expose. The template drops all capabilities except `NET_BIND_SERVICE`
and sets `no-new-privileges`.

## License

This repository is licensed under the terms in [LICENSE](LICENSE).
