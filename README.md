# otdp-sdk-react-native — React Native SDK for the Open Timetable Data Protocol

> Drop-in React Native SDK to display and subscribe to OTDP feeds in any iOS / Android app.

**Status:** Pre-development. Implementation begins 2026 Q4.
**License:** MIT
**Spec:** [otdp-spec](https://github.com/Timeble-org/otdp-spec)
**Maintainer:** [Timeble-org](https://github.com/Timeble-org)

---

## What this is

A permissively licensed React Native SDK that any mobile app can embed to consume Open Timetable Data Protocol feeds — clubs, festivals, raves, any live electronic music event.

The SDK handles:

- Subscribing to one or many OTDP feeds.
- Real-time delta synchronisation (Server-Sent Events, with offline fallback).
- Signature verification (Ed25519) — consumers can trust that an update came from the legitimate organiser.
- Background sync on iOS and Android.
- A minimal headless API — UI is left to the consuming app. Optional reference UI components ship separately.

## Why a dedicated SDK

Live event apps repeatedly solve the same problems poorly:

- Polling timetables that change every few minutes wastes battery and bandwidth.
- Festival 4G is unreliable; sync must be resilient.
- Time-zone and DST edge cases around all-night sets are a silent source of bugs.
- Trust: without signing, "the schedule changed" is indistinguishable from a rumour.

This SDK solves these once, in one place, for the whole ecosystem.

## Install (planned)

```bash
npm install @otdp/sdk-react-native
```

## Example usage (planned)

```typescript
import { OTDPClient } from '@otdp/sdk-react-native';

const client = new OTDPClient({
  feeds: ['https://feed.festivalmalta.com/otdp/2026'],
  verifySignatures: true,
});

client.on('update', (timetable) => {
  // render whatever UI you want
});

await client.connect();
```

## Roadmap

| Milestone | Target |
|---|---|
| Core client + pull sync | 2026 Q4 |
| SSE delta sync | 2026 Q4 |
| Signature verification | 2027 Q1 |
| iOS + Android background sync parity | 2027 Q1 |
| Reference UI components (optional package) | 2027 Q1 |
| v1.0 on npm | 2027 Q2 |

## Funding

Development is supported by an application to the [NGI Zero Commons Fund](https://nlnet.nl/commonsfund/) (NLnet, European Commission NGI programme).

## Relationship to Timeble

[Timeble](https://timeble.app) — the electroparty app — is the first commercial consumer of this SDK and serves as its primary real-world testbed. The SDK itself is fully independent: any app, including direct competitors, can use it without restriction.

This follows the established pattern of open protocols underpinning commercial products: Spotify on open audio codecs, Airbnb on OpenStreetMap, Shopify on open web standards. The protocol is shared infrastructure. The product is where companies compete.

## Contact

hello@timeble.app
