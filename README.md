# global-weather-service

A complete OpenClaw weather skill powered by Open-Meteo.

## Features

- Global city weather lookup
- Chinese formatted weather bulletin output
- Clothing, exercise, cold-risk, UV, and travel advice
- Scheduled weather subscriptions through OpenClaw cron
- Subscription management: create, list, update, delete
- Supports today, tomorrow, and 7-day forecast modes
- No API key required

## Structure

- `SKILL.md`: skill instructions and usage guidance
- `scripts/weather_report.py`: one-time weather query formatter
- `scripts/manage_weather_subscription.py`: subscription and timezone manager
- `data/subscriptions.json`: subscription state
- `data/user_timezones.json`: per-user timezone state

## Data source

- [Open-Meteo](https://open-meteo.com/)

## Example usage

### Query weather

```bash
python scripts/weather_report.py "南京" --days 7
python scripts/weather_report.py "London" --days 1
```

### Set timezone

```bash
python scripts/manage_weather_subscription.py set-timezone --to "qqbot:c2c:YOUR_ID" --timezone "Asia/Shanghai"
```

### Create subscription

```bash
python scripts/manage_weather_subscription.py add --to "qqbot:c2c:YOUR_ID" --city "南京" --time "每天晚上10点30分" --mode tomorrow
```

### List subscriptions

```bash
python scripts/manage_weather_subscription.py list --to "qqbot:c2c:YOUR_ID"
```

### Remove subscription

```bash
python scripts/manage_weather_subscription.py remove --name "天气订阅: 南京 明天天气"
```

## Notes

- The skill is designed for OpenClaw environments.
- Scheduled delivery relies on OpenClaw cron and channel routing.
- For QQ delivery, targets should use the `qqbot:c2c:<id>` form.
