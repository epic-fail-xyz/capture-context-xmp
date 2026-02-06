# Weather Capture Context XMP Specification — Version 1.0

🟧 Status: Draft — Implementation Feedback Welcome

## Namespace
> https://xmp.epic-fail.xyz/weather/1.0/

Preferred prefix: `wx`

This namespace is immutable once published.

## Scope

This specification defines a minimal set of atmospheric observations that may be embedded into digital media to describe environmental conditions at capture time.

The schema prioritizes:
* long-term interpretability
* scientific usefulness
* cross-platform survivability

Forecast data and UI-derived metrics are intentionally excluded.

## Design Principles
### Archival First

Metadata should remain understandable without requiring the originating service.

### Observational Truth

Fields describe measured or modeled conditions — not interpretations.

### SI Units Only

All numeric measurements use metric units.

### Store Primitives

Derived values (e.g., “feels like”) are excluded.

### Acquisition Transparency

Observation method and distance are included when available.

### Minimal Surface Area

Smaller schemas are more resilient across media pipelines.

## Required Fields
### wx:observationTime

Type: ISO 8601 UTC timestamp
Description: Time the observation represents.

### wx:observationSource

Type: Closed vocabulary
```
station
satellite
radar
modeled
interpolated
personalSensor
```

### wx:temperatureC

Type: Real number (°C)

## Strongly Recommended Fields
### wx:skyCondition
```
clear
few
scattered
broken
overcast
obscured
```

### wx:precipitationType
```
none
rain
snow
sleet
freezingRain
hail
mixed
```

### wx:visibilityMeters

Integer.

## Optional High-Value Fields
* wx:humidityPercent
* wx:windSpeedMps
* wx:windDirectionDegrees
* wx:pressureHpa

## Acquisition Context

These fields improve interpretability but are not required.
* wx:dataProvider
* wx:providerStationId
* wx:observationDistanceMeters
* wx:observationMethod
* wx:lookupTime
* wx:confidencePercent

## Example
```
<rdf:Description rdf:about=""
 xmlns:wx="https://xmp.epic-fail.xyz/weather/1.0/">

 <wx:observationTime>2026-02-05T22:00:00Z</wx:observationTime>
 <wx:observationSource>station</wx:observationSource>
 <wx:temperatureC>6.2</wx:temperatureC>
 <wx:skyCondition>overcast</wx:skyCondition>
 <wx:dataProvider>NOAA</wx:dataProvider>

</rdf:Description>
```

## Non-Goals

The specification intentionally excludes:
* forecasts
* hourly projections
* icons
* comfort indices
* provider-specific condition codes

## Payload Guidance

Typical payload size should remain well under 1KB.

Embedding large datasets is discouraged.

## Versioning Policy

Published namespaces are never modified.

Future revisions will appear at new paths:
```
/weather/1.1/
/weather/2.0/
```

Latest version:
https://xmp.epic-fail.xyz/weather/latest

## Implementation Guidance

Implementers should prefer:

* nearest-observation selection
* transparent interpolation
* accurate timestamps

Rounded lookup coordinates should not replace original capture GPS data.

## License
CC0 (Public Domain)
