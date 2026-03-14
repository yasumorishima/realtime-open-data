# Realtime Open Data

Real-time open data visualization projects running 24/7 on Raspberry Pi 5.

Each project collects publicly available data streams, stores them in SQLite, and serves interactive dark-themed maps via FastAPI + Leaflet.js.

## Projects

### Active

| Project | Data Source | Status |
|---|---|---|
| [**Persian Gulf Ship Tracker**](https://github.com/yasumorishima/hormuz-ship-tracker) | [aisstream.io](https://aisstream.io/) (AIS) | Collecting |

### Planned

| Project | Data Source | Description |
|---|---|---|
| ADS-B Flight Tracker | [OpenSky Network](https://opensky-network.org/) | Real-time aircraft positions, including military flights |
| Chokepoint Ship Tracker | [aisstream.io](https://aisstream.io/) | Suez Canal, Strait of Malacca, Taiwan Strait |
| Earthquake Monitor | [USGS Earthquake API](https://earthquake.usgs.gov/fdsnws/event/1/) | Global earthquakes in near real-time |
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

Designed to run on low-power hardware (Raspberry Pi 5, 8GB RAM) inside Docker containers.

## License

MIT
