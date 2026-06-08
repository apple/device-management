# Device Management Client Schema

This repository contains Apple's Device Management Client schema data for the MDM (Mobile Device Management) protocol, and the Declarative Device Management feature.

## OS Versions

This release corresponds to the following OS versions

| OS       | Version |
|----------|---------|
| iOS      | 27.0    |
| macOS    | 27.0    |
| tvOS     | 27.0    |
| visionOS | 27.0    |
| watchOS  | 27.0    |

See [Changes](CHANGES.md) for the significant changes in this release.

## What's Available

The following schema items are available:

* MDM commands - `mdm/commands`
* MDM check-in requests - `mdm/checkin`
* MDM profiles - `mdm/profiles`
* MDM errors - `mdm/errors`

* Declarative device management declarations - `declarative/declarations`
* Declarative device management status items - `declarative/status`
* Declarative device management protocol - `declarative/protocol`

* Other device management data formats

* Examples for schema items - `examples`
    * This directory contains `declarative`, `mdm`, and `other` directories.
    * Each sub-directory contains directories and files that mirror the structure of the corresponding schema directories.
    * Each schema item has its own directory containing the example files for the schema object.
    * Each YAML schema file contains an `examples` key that includes relative file paths to its example files.

## YAML Schema Definition

See [YAML Schema](docs/schema.md).

## Providing Feedback

All feedback on the data in this repository should be made using the `Feedback Assistant` app or website (https://feedbackassistant.apple.com). Select feedback for `Enterprise & Education`, and choose the `Mobile Device Management (MDM)` area.

We will NOT be accepting pull requests on this repository - please use `Feedback Assistant` for all requests.
