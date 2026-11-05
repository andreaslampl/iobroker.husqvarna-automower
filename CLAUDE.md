# ioBroker.husqvarna-automower (owner's fork)

Fork of ice987987/ioBroker.husqvarna-automower (MIT, keep the attribution), based on upstream main 0.6.0-beta.12.
Owner's mower: Automower 320 (GPS, work areas, stay-out zones, canConfirmError; no headlights). Used by the
SmartView robot tile (ioBroker.smartview, `www/robotlogic.js` template).

## Changes in this fork (0.6.0-beta.13)

- `stayOutZones.<zone>.name` / `.enable` (switch; `createStayOutZones()` / `updateStayOutZones()`); writing enable ->
  PATCH `/mowers/<id>/stayOutZones/<zoneId>` `{data: {type: 'stayOutZone', id, attributes: {enable}}}`; not possible
  while `stayOutZones.dirty`. Mower data is read again 5 s after the command (the cloud does not push zones).
- `ACTIONS.CONFIRMERROR` (if capabilities.canConfirmError) -> POST `/mowers/<id>/errors/confirm`.
- STARTINWORKAREA read `StartInWorkArea.*` (wrong case) -> `startInWorkArea.*`; work area 0 and duration 0 allowed.
- Endpoints checked against openHAB's automower binding (AutomowerConnectApi.java). Not yet tried on the real mower.
- `npm test`: test:js fails already upstream ("fn is not a function"); `npm run test:package` passes.

## Conventions

- Code and comments in English, like upstream. Bump `version` in package.json and io-package.json + news.
- Install: `iobroker url https://github.com/andreaslampl/ioBroker.husqvarna-automower`.
- Keep changes small so they can go upstream as a pull request.
