# \[Work In Progress\] AMWA IN-005: \[Timing\] Principles of External Signal Ingress for DMF Media Workloads

[![Lint Status](https://github.com/AMWA-TV/in-005/actions/workflows/lint.yml/badge.svg)](https://github.com/AMWA-TV/in-005/actions/workflows/lint.yml)
[![Zensical Render Status](https://github.com/AMWA-TV/in-005/actions/workflows/docs.yml/badge.svg)](https://github.com/AMWA-TV/in-005/actions/workflows/docs.yml)
[![License](https://img.shields.io/github/license/AMWA-TV/in-005)](https://github.com/AMWA-TV/in-005/blob/HEAD/LICENSE)
[![Issues](https://img.shields.io/github/issues/AMWA-TV/in-005)](https://github.com/AMWA-TV/in-005/issues)

This repository holds the source of a work artifact published as an **[AMWA Increment (IN)](https://specs.amwa.tv/in-index)** from the [Advanced Media Workflow Association](https://amwa.tv)

<!-- INTRO-START -->

### What does it do?

- Defines principles for ingesting external media Signals into a Dynamic Media Facility (DMF) Media Workload and conforming them into usable, time-aligned Flows.
- Identifies the timing provenance, metadata, and registry information needed to manage Signals as they enter the Media Workload.

### Why does it matter?

- External Signals may have different frequency and timestamp provenance, so consistent ingress conformance is needed to align media Flows and support interoperable processing.
- Clear conformance principles help avoid unnecessary buffering and make timing adjustments traceable.

### How does it work?

- Uses Signal frequency and timestamp provenance, together with the Media Workload clock, to determine how Indexing Time Stamps are created or adjusted.
- Applies frame synchronisation or audio sample-rate conversion when required, and records relevant Signal attributes and timing offsets in an ingress registry.

This work artifact is published as an **AMWA Increment (IN)**. Increments are intended to make public the ongoing progress of a working group without locking decisions into a formal specification. While the technical details contained in this repository do not constitute a stable or finalized specification, readers should note that Increments are Draft Specifications as defined in the AMWA IPR Policy. The provisions of the policy apply, including the requirement for early disclosure. You can expect the content to evolve incrementally based on ongoing testing, consensus-building, and community input. Public review is encouraged! Please post an Issue to the Repo to submit questions, feedback, or propose changes.


<!-- INTRO-END -->
