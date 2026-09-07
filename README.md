# Crop Steering Controller for Home Assistant

The companion irrigation controller for [Crop Steering](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy). This repository supports existing Home Assistant app installations and receives the matching controller release.

**[Try the interactive demo](https://jaketherabbit.github.io/HA-Irrigation-Strategy/dashboard.html?demo=1)** · **[Install and upgrade guide](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy/blob/main/docs/INSTALL.md)**

![Native Crop Steering workspace](https://raw.githubusercontent.com/JakeTheRabbit/HA-Irrigation-Strategy/main/img/operator-dashboard.png)

## Install

1. [Install the Crop Steering integration through HACS](https://my.home-assistant.io/redirect/hacs_repository/?owner=JakeTheRabbit&repository=HA-Irrigation-Strategy&category=integration), then restart Home Assistant and add Crop Steering in Devices & services.
2. [Add this controller app repository](https://my.home-assistant.io/redirect/supervisor_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FJakeTheRabbit%2Ff2-control). Install **Crop Steering Controller**, review its options and start it.
3. Open **Crop Steering** in the sidebar. Use **Rooms & setup** to map each room's pump, mainline, valves and probes, then enter pot size, plant count and dripper output. The controller adopts the integration's mapping.
4. Check fresh sensor readings, controller heartbeat, current setpoints and safety holds. Commission actual water delivery before enabling irrigation.

Integration **2.13.0** pairs with controller **0.12.0**. Home Assistant OS/Supervised provides the app store and internal authentication. No token needs to be committed to a file.

## Upgrade an existing controller

Use **Update** on the controller you already installed. Keep its repository and app identity so Supervisor preserves `/data/state.json`, options and counters. Installing another copy from the main project repository creates a separate controller instance.

Update the companion integration as well and restart Home Assistant. A plain controller restart reuses the old image; a published Update or local-source Rebuild loads the new code. Verify versions, heartbeat and restored settings afterwards. Do not re-enter defaults over your current setpoints.

Feed EC/pH sources and hold entities remain installation-specific options. Empty feed-probe mappings disable those particular gates; map your own reservoir probes to use them. Weekly water is a controller delivery estimate, with partial-history coverage after upgrade, rather than measured flow.

## Source and documentation

This repository contains the packaged controller. Development happens in [HA-Irrigation-Strategy](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy); release tooling copies only tracked runtime files and the current dashboard.

- [Controller changelog](f2_control/CHANGELOG.md)
- [Controller operation](f2_control/DOCS.md)
- [Whole-grow planning](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy/blob/main/docs/GROW_PLANS.md)
- [Validated features and limits](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy/blob/main/docs/FEATURE_MATRIX.md)
