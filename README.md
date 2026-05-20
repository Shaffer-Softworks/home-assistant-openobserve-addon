# Home Assistant OpenObserve Log Shipper (Add-on)

Supervisor add-on that tails `home-assistant.log` and forwards lines to [OpenObserve](https://openobserve.ai/) via Fluent Bit.

Requires **Home Assistant OS** (Supervisor). Does not run in a plain `home-assistant` Docker container.

## Related repo

For core logs and HA bus events (config flow, HACS), use the integration:

**https://github.com/Shaffer-Softworks/home-assistant-openobserve**

| Source | Stream (suggested) | Ingest |
|--------|-------------------|--------|
| Integration | `home_assistant_logs`, `home_assistant_events` | `/_json` |
| This add-on | `home_assistant_supervisor` | `/_multi` |

## Install

1. **Settings → Add-ons → Add-on store → ⋮ → Repositories**
2. Add `https://github.com/Shaffer-Softworks/home-assistant-openobserve-addon`
3. Install **OpenObserve Log Shipper** and start it

## Configuration

| Option | Example |
|--------|---------|
| `openobserve_url` | `http://10.20.0.54:5080/api/default/home_assistant_supervisor/_multi` |
| `openobserve_username` | your OpenObserve user |
| `openobserve_password` | your OpenObserve password |
| `log_path` | `/config/home-assistant.log` |

Use the full ingest URL including `/_multi` (NDJSON). The HACS integration uses `/_json` instead.

## Verify

```sql
SELECT * FROM home_assistant_supervisor ORDER BY _timestamp DESC LIMIT 20
```

## Icon attribution

From [Dashboard Icons — open-observe](https://dashboardicons.com/icons/open-observe) (homarr-labs/dashboard-icons, Apache-2.0).

## License

MIT. Icon assets: Apache-2.0 per Dashboard Icons.
