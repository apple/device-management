# Schema Errata

This document lists errata for the YAML schema. This is used when older versions of the schema are incorrect, and a fix was made in later schema to correct the problem.

## iOS 17 / macOS 14

### profiles/com.apple.vpn.managed.yaml

The `CertificateType` key in the `com.apple.vpn.managed` profile payload incorrectly listed `Ed25519` as a supported certificate type. That type was never supported and has now been removed.

The `PPTP` VPNType has not been supported since iOS 10 and macOS 10.12, see https://support.apple.com/en-us/HT206844. The `PPTP` VPNType has been removed.

### mdmprotocol/commands passcode.firmware.set.yaml passcode.firmware.verify.yaml

The response keys were incorrectly listed as being top-level keys in the response dictionary when in fact they were nested one-level deep.

### profiles/com.apple.vpn.managed.applayer.yaml

The `OnDemandMatchAppEnabled` key in the `com.apple.vpn.managed.applayer` profile payload incorrectly listed its type as `integer`. The correct type is `boolean`.

### profiles/com.apple.wifi.managed.yaml

The EAPClientConfiguration dictionary listed both OneTimePassword and OneTimeUserPassword as valid keys. The erroneous OneTimePassword key has been removed.

### profiles/com.apple.security.scep.yaml

The documentation indicated that all the keys in the SubjectAltName value could be either string or array types. The ntPrincipalName cannot be an array and must be a
string. This has been clarified in the description. Note that the type field for the rfc822Name, dNSName, and uniformResourceIdentifier still indicates these are
strings. This has not been corrected as the schema does not support polymorphic types.

### profiles/com.apple.universalaccess.yaml

The `contrast` key in the `com.apple.universalaccess` profile payload incorrectly listed its type as `integer`. The correct type is `real`.
