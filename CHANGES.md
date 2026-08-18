# Changes

Significant changes in this release.

---

## declarative/declarations/configurations

### New Objects

- New: declarative/declarations/configurations/accessibility.settings.yaml
- New: declarative/declarations/configurations/app.settings.yaml
- New: declarative/declarations/configurations/content-cache.settings.yaml
- New: declarative/declarations/configurations/extensible-sso.yaml
- New: declarative/declarations/configurations/network.dns-proxy.yaml
- New: declarative/declarations/configurations/network.dns-settings.yaml
- New: declarative/declarations/configurations/network.relay.yaml
- New: declarative/declarations/configurations/network.vpn.always-on.yaml
- New: declarative/declarations/configurations/network.vpn.ikev2.yaml
- New: declarative/declarations/configurations/network.vpn.ipsec.yaml
- New: declarative/declarations/configurations/network.vpn.vpn-plugin.yaml
- New: declarative/declarations/configurations/webcontent-filter.plugin.yaml

### New Payload Keys

- New: declarative/declarations/configurations/intelligence.settings.yaml/AllowVisualIntelligence
- New: declarative/declarations/configurations/intelligence.settings.yaml/Apps/Calendar
- New: declarative/declarations/configurations/legacy.interactive.yaml/ProfileAssetReference
- New: declarative/declarations/configurations/legacy.yaml/ProfileAssetReference
- New: declarative/declarations/configurations/package.yaml/UninstallBehavior
- New: declarative/declarations/configurations/safari.settings.yaml/Privacy
- New: declarative/declarations/configurations/siri.settings.yaml/AllowSiriAI
- New: declarative/declarations/configurations/siri.settings.yaml/ForceReduceSensitiveContent

### Objects with New OS Support

- Changed: declarative/declarations/configurations/siri.settings.yaml [tvOS 27.0]

### Payload Keys with New OS Support

- Changed: declarative/declarations/configurations/app.managed.yaml/AppConfig [macOS 27.0]
- Changed: declarative/declarations/configurations/app.managed.yaml/ExtensionConfigs [macOS 27.0]
- Changed: declarative/declarations/configurations/app.managed.yaml/LegacyAppConfigAssetReference [macOS 27.0]

### Removed Payload Keys

- Removed: declarative/declarations/configurations/app.managed.yaml/VPPType

---

## declarative/status

### New Objects

- New: declarative/status/content-cache.info.yaml
- New: declarative/status/content-cache.parents.yaml
- New: declarative/status/content-cache.peers.yaml
- New: declarative/status/content-cache.status.yaml
- New: declarative/status/device.system.health.yaml
- New: declarative/status/enhanced-logging.applecare-token.yaml
- New: declarative/status/enhanced-logging.status.yaml
- New: declarative/status/enhanced-logging.timestamp.yaml
- New: declarative/status/mdm.enrollment-type.yaml
- New: declarative/status/mdm.is-awaiting-configuration.yaml
- New: declarative/status/mdm.is-return-to-service.yaml
- New: declarative/status/mdm.is-shared-ipad.yaml
- New: declarative/status/mdm.push-magic.yaml
- New: declarative/status/mdm.push-token.yaml
- New: declarative/status/security.lockdown-mode.yaml

### Payload Keys with New OS Support

- Changed: declarative/status/app.managed.list.yaml/app.managed.list/status_value/config-state [macOS 27.0]

---

## mdm/checkin

### New Payload Keys

- New: mdm/checkin/returntoservice.yaml/ReturnToService/ShouldRetryEnrollment

---

## mdm/commands

### New Objects

- New: mdm/commands/cancel.enhanced.log.collection.yaml
- New: mdm/commands/trigger.enhanced.log.collection.yaml

### New Payload Keys

- New: mdm/commands/device.erase.yaml/ReturnToService/ShouldRetryEnrollment

### Removed Objects

- Removed: mdm/commands/system.update.available.yaml
- Removed: mdm/commands/system.update.scan.yaml
- Removed: mdm/commands/system.update.schedule.yaml
- Removed: mdm/commands/system.update.status.yaml

### Removed Payload Keys

- Removed: mdm/commands/information.device.yaml/Queries/OSUpdateSettings
- Removed: mdm/commands/information.device.yaml/Queries/SoftwareUpdateDeviceID
- Removed: mdm/commands/information.device.yaml/Queries/SoftwareUpdateSettings
- Removed: mdm/commands/information.device.yaml/QueryResponses/SoftwareUpdateDeviceID
- Removed: mdm/commands/information.device.yaml/QueryResponses/SoftwareUpdateSettings
- Removed: mdm/commands/settings.yaml/Settings/SoftwareUpdateSettings

---

## mdm/profiles

### New Payload Keys

- New: mdm/profiles/com.apple.applicationaccess.yaml/allowSiriAI
- New: mdm/profiles/com.apple.extensiblesso.yaml/PlatformSSO/AllowWebLoginPasswordSync
- New: mdm/profiles/com.apple.extensiblesso.yaml/PlatformSSO/WebLoginURLAllowList
- New: mdm/profiles/com.apple.loginwindow.yaml/ForceCaptivePortalConnectionFromLockScreen
- New: mdm/profiles/com.apple.loginwindow.yaml/ForceWifiConfigurationOnLockScreen

### Payload Keys with New OS Support

- Changed: mdm/profiles/com.apple.applicationaccess.yaml/allowAutomaticAppDownloads [visionOS 27.0]
- Changed: mdm/profiles/com.apple.applicationaccess.yaml/allowCamera [visionOS 27.0]
- Changed: mdm/profiles/com.apple.applicationaccess.yaml/allowListedAppBundleIDs [visionOS 27.0]
- Changed: mdm/profiles/com.apple.applicationaccess.yaml/blockedAppBundleIDs [visionOS 27.0]

### Removed Objects

- Removed: mdm/profiles/com.apple.SoftwareUpdate.yaml

### Removed Payload Keys

- Removed: mdm/profiles/com.apple.applicationaccess.yaml/allowRapidSecurityResponseInstallation
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/allowRapidSecurityResponseRemoval
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/enforcedSoftwareUpdateDelay
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/enforcedSoftwareUpdateMajorOSDeferredInstallDelay
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/enforcedSoftwareUpdateMinorOSDeferredInstallDelay
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/enforcedSoftwareUpdateNonOSDeferredInstallDelay
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/forceDelayedAppSoftwareUpdates
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/forceDelayedMajorSoftwareUpdates
- Removed: mdm/profiles/com.apple.applicationaccess.yaml/forceDelayedSoftwareUpdates
- Removed: mdm/profiles/com.apple.system.logging.yaml/Processes

### Renamed Objects

- Renamed: mdm/profiles/com.apple.MCX(Mobililty).yaml -> mdm/profiles/com.apple.MCX(Mobility).yaml

---

## mdm/errors

No changes.

---

## other

### New Payload Keys

- New: other/skipkeys.yaml/AccessibilityAppearance
- New: other/skipkeys.yaml/DeviceFeaturesTour
- New: other/skipkeys.yaml/LiquidGlass

---

## openapi

### New Objects

- New: openapi/content-cache/metrics_report.json
