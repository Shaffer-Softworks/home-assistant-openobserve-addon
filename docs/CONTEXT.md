# Project context — Supervisor add-on repo

Split from monorepo on 2026-05-20. **HACS integration** is [home-assistant-openobserve](https://github.com/Shaffer-Softworks/home-assistant-openobserve).

## Scope

- `openobserve_log_shipper/` — Fluent Bit add-on for HA OS
- `repository.yaml` — add-on store entry

## Ingest

- `/_multi` (NDJSON) to stream `home_assistant_supervisor`
- Tails `/config/home-assistant.log` (config mount read-only)

## Not supported

Plain `home-assistant` Docker container (no Supervisor).
