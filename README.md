# f2-control — retired

This repository is archived and gets no more releases.

The Crop Steering controller app is now installed only from
**[JakeTheRabbit/HA-Irrigation-Strategy](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy)**
(`addons/f2_control`). This repository was a published copy of that folder.

**Installed the controller from here?** Move it once: install the app from HA-Irrigation-Strategy,
copy the old app's options and its `/data/state.json` across (it holds each zone's phase, today's
counters, the accepted setup and what Auto Setpoints has learned), then uninstall this one. Never run
both at the same time: they would drive the same pump and valves. Step-by-step:
[docs/INSTALL.md — Moving a controller installed from f2-control](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy/blob/main/docs/INSTALL.md#moving-a-controller-installed-from-f2-control).

The last release published here was controller **0.16.2**, identical to `addons/f2_control` at
HA-Irrigation-Strategy `v2.19.2`.
