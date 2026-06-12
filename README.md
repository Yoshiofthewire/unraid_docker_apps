# Unraid Community Applications Templates

This repository contains XML templates for publishing and maintaining Unraid Community Applications (CA) entries.

## What Is In This Repo

- [ca_profile.xml](ca_profile.xml): Maintainer profile metadata used by CA.
- [hrhomerun.xml](hrhomerun.xml): Template for the HDHomeRun DVR container.
- [lumolabels.xml](lumolabels.xml): Template for the Lumo Labels container.

## Included Templates

### HDHomeRunDVR

- XML file: [hrhomerun.xml](hrhomerun.xml)
- Container repository: yoshiofthewire/hdhomerundvr
- Network mode: host
- Typical usage: run SiliconDust HDHomeRun DVR engine with host networking for discovery
- Support thread: https://forums.unraid.net/topic/199378-support-hdhomerun-dvr-20250815/

Main template fields in this file include:

- Required host path mapping for DVR data
- UDP port mapping for 65001
- Links to project and upstream README

### LumoLabels

- XML file: [lumolabels.xml](lumolabels.xml)
- Container repository: yoshiofthewire/lumo-labels
- Network mode: bridge
- Web UI: [http://IP:5866](http://IP:5866)
- Typical usage: Proton Mail auto-labeling with a local Lumo model
- Support thread: https://forums.unraid.net/topic/199419-support-lumo-labels-gmail-sorting-for-proton-mail/

Main template fields in this file include:

- TCP Web UI port mapping on 5866
- Appdata path mappings for config, state, and logs
- Links to project and upstream README


## License

This repository is licensed under the terms in [LICENSE](LICENSE).

