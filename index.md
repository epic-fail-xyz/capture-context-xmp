# Capture Context XMP Specifications

🟧 Project Status: Active — Early Draft Specifications

The Capture Context XMP project defines open metadata specifications describing the environmental conditions surrounding the capture of digital media.

These specifications are designed for long-term interpretability, scientific usefulness, and cross-platform compatibility.

They aim to preserve context, not merely pixels.

## Why Capture Context?

Digital media typically preserves:
* camera settings
* timestamps
* location

Yet the surrounding environment — weather, atmosphere, and physical conditions — is rarely recorded in a structured, durable way.

Capture Context XMP addresses this gap.

By embedding observational metadata directly into media files, the specifications support:
* archival preservation
* scientific datasets
* search and filtering
* machine learning pipelines
* forensic reconstruction
* environmental analysis

without requiring proprietary services.

## Specifications
### Stable / In Development

Weather Capture Context XMP - Version 1.0 (Draft)
`/weather/1.0/`

Additional environmental modules are expected over time.

## Design Goals

The project follows several guiding principles:
* **Archival-first** - metadata should remain interpretable decades into the future.
* **Observational truth** — store measured conditions, not UI summaries.
* **SI units* — ensure global analytical compatibility.
* **Minimalism* — smaller schemas survive real-world media pipelines.
* **Immutable versioning* — published namespaces are never modified.
* **Open by default* — specifications are intended for universal adoption.

## Governance

This project is currently maintained by its original author.

The long-term goal is stability rather than rapid expansion.
Backward compatibility is prioritized.

Breaking changes will only occur through new namespace versions.

Community feedback is welcome as real-world implementations emerge.

## License

All specifications are released under CC0 (Public Domain) to eliminate barriers to adoption.

## Status Philosophy

These documents are published as open specifications.

Standardization is expected to occur organically through real-world usage rather than formal process.
