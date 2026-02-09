# Weather Capture Context XMP Specification — Version 1.0

🟦 Status: Candidate Recommendation

## Namespace
> https://xmp.epic-fail.xyz/weather/1.0/

Preferred prefix: `wx`

This namespace is immutable once published.
Corrections or extensions will appear only in subsequent versioned namespaces.

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

## Terminology

**Observation** — Measured or modeled atmospheric conditions associated with a specific timestamp.

**Capture Location** — Geographic position where the media was created.

## Required Fields
### wx:observationTime
* **Type**: ISO 8601 UTC timestamp
* **Description**: Timestamp representing when the atmospheric conditions were observed or modeled, not when the data was retrieved.

### wx:observationSource
* **Type**: Closed enumeration
```
station
satellite
radar
modeled
interpolated
personalSensor
```

### wx:temperatureC
* **Type**: Decimal (°C)
* **Description**: Precision is implementation-defined.

## Recommended Fields
### wx:skyCondition
* **Type**: Closed enumeration
```
clear
few
scattered
broken
overcast
obscured
```

### wx:precipitationType
* **Type**: Closed enumeration
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
* **Type**: Integer

## Recommended Extensions
### wx:humidityPercent
* **Type**: Integer (0–100)
* **Description**: Relative humidity at observation time.

### wx:windSpeedMps
* **Type**: Decimal
* **Description**: Sustained wind speed measured in meters per second.

### wx:windDirectionDegrees
* **Type**: Integer (0–360)
* **Description**: Direction from which the wind originates, expressed in degrees clockwise from true north.

### wx:pressureHpa
* **Type**: Decimal
* **Description**: Atmospheric pressure expressed in hectopascals.

## Acquisition Context Fields
These fields describe how the observation was obtained rather than the atmospheric conditions themselves.

These fields improve interpretability but are not required.

### wx:dataProvider
* **Type**: String
* **Description**: Organization or system that supplied the observation data.

### wx:providerStationId
* **Type**: String
* **Description**: Identifier assigned by the data provider to the observation station or source.

### wx:observationDistanceMeters
* **Type**: Decimal
* **Description**: Approximate spatial separation between capture location and observation source.

### wx:observationMethod
* **Type**: Extensible Enumeration

Suggested values:
```
direct
interpolated
modeled
blended
unknown
```

### wx:lookupTime
* **Type**: ISO 8601 UTC timestamp
* **Description**: Time at which the observation data was retrieved from the provider.

### wx:confidencePercent
* **Type**: Integer (0–100)
* **Description**: Provider- or implementation-estimated confidence in the observation accuracy.

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

## Out of Scope

The specification intentionally excludes:
* forecasts
* hourly projections
* icons
* comfort indices
* provider-specific condition codes

## Size Considerations

Implementations SHOULD keep payload size minimal to maximize compatibility across media pipelines.

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

When possible, implementers SHOULD prefer observational data over modeled data.

Consumers MUST ignore unknown fields within the namespace to preserve forward compatibility.

## License
CC0 (Public Domain)
