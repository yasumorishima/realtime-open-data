# Realtime Open Data

Real-time open data visualization projects running 24/7.

Each project collects publicly available data streams, stores them in SQLite, and serves interactive dark-themed maps via FastAPI + Leaflet.js.

## Projects

### Active

| Project | Data Source | Status |
|---|---|---|
| [**Persian Gulf Ship Tracker**](https://github.com/yasumorishima/hormuz-ship-tracker) | [aisstream.io](https://aisstream.io/) (AIS) | Collecting |
| [**Japan Geohazard Monitor**](https://github.com/yasumorishima/japan-geohazard-monitor) | JMA, USGS, AMeDAS, INTERMAGNET, etc. | In development |

### Planned

| Project | Data Source | Description |
|---|---|---|
| ADS-B Flight Tracker | [OpenSky Network](https://opensky-network.org/) | Real-time aircraft positions, including military flights |
| Chokepoint Ship Tracker | [aisstream.io](https://aisstream.io/) | Suez Canal, Strait of Malacca, Taiwan Strait |
| Japan Railway Delay Monitor | [ODPT](https://www.odpt.org/) | Real-time train delay/disruption visualization on route map |
| Wildfire Tracker | [NASA FIRMS](https://firms.modaps.eosdis.nasa.gov/) | Satellite-detected active fires worldwide |
| Lightning Tracker | [Blitzortung.org](https://www.blitzortung.org/) | Real-time lightning strike detection |
| Satellite Tracker | [CelesTrak TLE](https://celestrak.org/) | ISS, Starlink, and satellite orbit visualization |

## Architecture

All projects share a common pattern:

```
Real-time data source (WebSocket / API)
    → Land/boundary filter (Shapely + Natural Earth)
    → SQLite (batch insert + per-entity throttle)
    → FastAPI + Leaflet.js (dark-themed live map)
    → matplotlib snapshot → GitHub (auto-push)
```

Runs in Docker — on cloud or Raspberry Pi 5 depending on data volume and real-time requirements.

## License

MIT
