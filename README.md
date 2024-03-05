# Device Management Client Schema

This repository contains Apple's Device Management Client schema data for the MDM (Mobile Device Management) protocol, and the Declarative Device Management feature.

## OS Versions

This release corresponds to the following OS versions

| OS       | Version |
|----------|---------|
| iOS      | 17.4    |
| macOS    | 14.4    |
| tvOS     | 17.4    |
| visionOS |  1.1    |
| watchOS  | 10.4    |

## Important Release Notes

### visionOS support

The 17.4/14.4 release adds a `visionOS` value to the `supportedOS` key to indicate support for visionOS devices.

### Declarative device management supervision state

The 17.4/14.4 release includes a major change to the `allowed-enrollments` key in declarative device management schema items. A new `supervised` value has been added. So now:

* `supervised` is used to indicate support for a supervised device enrollment
* `device` is used to indicate support for an unsupervised device enrollment.

On macOS, device enrollments are always supervised, so the `device` value has been replaced by `supervised` in all `allowed-enrollments`.

On other platforms, `supervision` has been added or `device` has been removed, as appropriate for actual support.

### Declarative device management combinetype values

The 17.4/14.4 release has renamed the `enum-lowest` and `enum-highest` combinetype values to `enum-first` and `enum-last` respectively.

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

## YAML Schema Definition

See [YAML Schema](docs/schema.md).

## Providing Feedback

All feedback on the data in this repository should be made using the `Feedback Assistant` app or website (https://feedbackassistant.apple.com). Select feedback for `Enterprise & Education`, and choose the `Mobile Device Management (MDM)` area.

We will NOT be accepting pull requests on this repository - please use `Feedback Assistant` for all requests.
