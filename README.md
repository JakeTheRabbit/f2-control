# F2 Control — Home Assistant add-on repository

One-click install for the **f2-control** crop-steering engine — the autonomous P0→P1→P2→P3
irrigation controller from [HA-Irrigation-Strategy](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy).

## Install (one-click, by URL)

1. In Home Assistant: **Settings → Add-ons → Add-on Store → ⋮ (top-right) → Repositories**.
2. Paste this URL and **Add**:
   ```
   https://github.com/JakeTheRabbit/f2-control
   ```
3. Close the dialog — **F2 Control** now appears in the store. Open it → **Install**.

> This is the *add-on repository* — paste the URL above into the **Add-on Store → Repositories**
> dialog (not HACS, and not a subfolder URL).

## Install the integration first

The engine drives **only** the hardware you map in the companion **Crop Steering integration**
(entities + setup wizard + dashboards) — install it via HACS from the main repo *before* this
add-on, and map your pump, mainline and per-zone valves + sensors there. The add-on reads that map
from the integration; there are no facility defaults, so an add-on installed against no integration
holds safe (never waters) until it's set up. Full step-by-step:
**https://github.com/JakeTheRabbit/HA-Irrigation-Strategy** → `docs/AGENT_INSTALL.md`.

## After installing

1. **Kill switch.** Create `input_boolean.f2_control_enabled` (a Helper, or deploy
   `f2_control/f2_control_package.yaml` to `/config/packages` then reload). **OFF = safe** — the
   add-on reads, computes and notifies but never opens a valve.
2. **Configure** (add-on → Configuration). Everything here is optional:
   - `lights_on_hour` / `lights_off_hour` — fall back to these only until the integration's light
     entities are read.
   - `notify_service` — **blank = in-app persistent notifications only** (no phone push). There is
     no built-in default; it never texts a stranger's device.
   - `feed_ec_sensor` / `feed_ph_sensor` — your reservoir probes for the source-water gate. **Empty
     by default = that half of the gate is off** (no facility fallback). Set your own entity ids to
     enable feed gating.
   - `hold_entities` — a list of `input_boolean`/`switch` ids that pause irrigation while ON (tank
     fill, nutrient dosing, flush). Empty by default.

   The token is automatic (`homeassistant_api: true`).
3. **Start** it. The log shows `starting | … | token present: True`, then the effective timezone.
4. Watch a photoperiod with the kill switch OFF, then flip it ON to go live.

## Updating

The add-on bakes its code at build time, so when a new version ships, use the add-on's **Update**
(or **⋮ → Rebuild**) — a plain Restart keeps the old code.

---

*The add-on source is developed in the main monorepo at `addons/f2_control/` and published here on
each release (`scripts/publish_addon.sh`). File issues on the
[main repo](https://github.com/JakeTheRabbit/HA-Irrigation-Strategy/issues).*
