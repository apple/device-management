# Device Management Client YAML Schema Format

## Schema Definition

The definition of the schema used here is in the `schema.yaml` file. That file contains the YAML-encoded [JSON-schema](https://json-schema.org) representation of the schema definitions. Below are descriptions of the various elements of the schema and how they are used.

### Top Level Object

| Name         | Type   | Description |
|--------------|--------|-------------|
| title        | string | Title for this schema object |
| description  | string | Description of this schema object |
| payload      | object | Information about the object as a whole |
| payloadkeys  | array  | A list of YAML objects representing the command request |
| responsekeys | array  | A list of YAML objects representing the command response |
| reasons      | array  | A list of YAML objects representing declarative device management status reason codes |
| notes        | array  | A list of YAML objects representing additional notes for the schema item as a whole |

### Payload Object

| Name            | Type   | Description |
|-----------------|--------|-------------|
| payloadtype     | string | Type of the profile payload |
| requesttype     | string | Type of the MDM command |
| declarationtype | string | Type of the declaration payload |
| statusitemtype  | string | Type of the status payload |
| credentialtype  | string | Type of the credential asset data |
| supportedOS     | object | Identifies the range of supported OS versions that support the entire payload |
| apply           | string | Indicates how multiple configurations of the same type are applied |
| content         | string | Description of the payload |

### supportedOS Object

| Name     | Type   | Description |
|----------|--------|-------------|
| iOS      | object | Supported features on this iOS |
| macOS    | object | Supported features on this macOS |
| tvOS     | object | Supported features on this tvOS |
| visionOS | object | Supported features on this visionOS |
| watchOS  | object | Supported features on this watchOS |

__Notes__

The `supportedOS` object is used in the `payload` object to indicate overall support for this object on each OS, as well as which enrollment modes are supported per OS. The `supportedOS` key may also appear on any payload key defined in `payloadkeys` or `responsekeys` array item objects. Each payload key is assumed to "inherit" the `supportedOS` values from the `payload` object, but that is then updated with any items in the key's own `supportedOS` object if present. This also overriding specific values in `supportedOS` on a per-key basis without the need to duplicate the entire `supportedOS` value from the `payload`.

### iOS, macOS, tvOS, visionOS, watchOS Objects

| Name                | Type    | Description |
|---------------------|---------|-------------|
| introduced          | string  | OS version where feature was introduced |
| deprecated          | string  | OS version where feature was deprecated |
| removed             | string  | OS version where feature was removed |
| accessrights        | string  | The MDM protocol access rights required on the device to execute the command |
| multiple            | boolean | Indicates whether multiple copies of the payload can be installed |
| devicechannel       | boolean | Indicates whether the command or profile is supported on the device channel |
| userchannel         | boolean | indicates whether the command or profile is supported on the user channel |
| supervised          | boolean | Indicates whether the command or profile can only be executed on supervised devices |
| requiresdep         | boolean | If True, the command can only be executed on devices provisioned in DEP |
| userapprovedmdm     | boolean | If True, the command can only be executed on devices with user-approved MDM enrollment |
| allowmanualinstall  | boolean | If True, the profile can be installed manually by a user on the device |
| sharedipad          | object  | Additional behavior specific to shared iPad devices |
| userenrollment      | object  | Additional behavior when user enrollment is in effect |
| always-skippable    | boolean | If True, indicates that the skip key's corresponding Setup pane is always skipped. If False, indicates that the skip key's corresponding Setup pane may be shown, depending on exactly when during the setup flow it occurs. This is only used in skipkeys.yaml. |
| allowed-enrollments | string  | Array of allowed enrollment types for declarative device management |
| allowed-scopes      | string  | Array of allowed enrollment scopes for declarative device management |

### Shared iPad Object

| Name           | Type    | Description |
|----------------|---------|-------------|
| mode           | string  | Indicates whether a payload or payload key can used with shared iPad |
| devicechannel  | boolean | Defines if the payload can be installed on the device MDM channel |
| userchannel    | boolean | Defines if the payload can be installed on the user MDM channel |
| allowed-scopes | string  | Array of allowed enrollment scopes for declarative device management |

__Notes__

The `mode` can have one of four values: `allowed`, `required`, `forbidden`, and `ignored`. If set to `allowed`, then the payload or payload key can be used both with or without shared iPad in effect. If set to `required`, then the payload or payload key can only be used if shared iPad is in effect. If set to `forbidden`, then the payload or payload key cannot be used if shared iPad is in effect. If set to `ignored`, then the payload or payload key can be used, but is ignored if shared iPad is in effect.

### User Enrollment Object

| Name     | Type   | Description |
|----------|--------|-------------|
| mode     | string | Indicates how a payload or payload key can only be used if user enrollment is in effect |
| behavior | string | Describes any special behavior for the payload or payload key if user enrollment is in effect |

__Notes__

The `mode` can have one of four values: `allowed`, `required`, `forbidden`, and `ignored`. If set to `allowed`, then the payload or payload key can be used both with or without user enrollment in effect. If set to `required`, then the payload or payload key can only be used if user enrollment is in effect. If set to `forbidden`, then the payload or payload key cannot be used if user enrollment is in effect. If set to `ignored`, then the payload or payload key can be used, but is ignored if user enrollment is in effect.

### Payload/Response Keys Array Object

| Name        | Type   | Description |
|-------------|--------|-------------|
| key         | string | The name of the key |
| title       | string | The title of the key |
| supportedOS | object | Identifies the range of supported OS versions that support the key |
| type        | string | The type of key |
| subtype     | string | Indicates the expected format of the string value of the key (deprecated) |
| valuetype   | string | Indicates the expected format of the string value of the key |
| assettypes  | array  | Indicates the set of allowed asset types |
| presence    | string | Whether the key is required or optional |
| rangelist   | array  | List of allowed values for this key |
| range       | object | Bounds for the value of this key |
| default     | scalar | The default value for the key |
| format      | string | The format for the value expressed as a regular expression |
| repetition  | object | Cardinality for this value |
| combinetype | string | Indicates how this key is combined with ones from other configurations |
| content     | string | Description of the payload key |
| subkeytype  | string | A name that uniquely represents the structured subkey object |
| subkeys     | array  | An array of payload keys |

__Notes__

The `subtype` key is deprecated in favor of the `valuetype` key.

The `presence` value must be one of: `required` or `optional`.

#### Type Values

| Name          | Description |
|---------------|-------------|
| \<string>     | A string value |
| \<integer>    | An integer value |
| \<real>       | A real value |
| \<boolean>    | A boolean value |
| \<date>       | A date value (deprecated) |
| \<data>       | A data value |
| \<array>      | An array value |
| \<dictionary> | A dictionary value |
| \<any>        | Any standard value |

__Notes__

If the `<string>` value is used, the `valuetype` key may also be specified to define a specific format for the string (see below).

The value `<any>` may be used to indicate that any of the standard values can be used without any expectation that the value will be validated.

The `<date>` value is deprecated. Instead `<string>` will be used with a suitable `<valuetype>` set to indicate one of several date-time formats.

#### Valuetype Values

`domain`
: The string value is a domain name. This is an exact match (i.e., `example.com` will match `example.com` and will not match `test.example.com`, `1example.com`, `example.com2`).

`domain-prefix`
: The string value is a domain name pattern, with matching rules as follows:
* If the string starts with a `*.`, the pattern will match any sub-domain of the parent domain, but not the parent domain itself (i.e., `*.example.com` will match `test.example.com` and will not match `example.com`, `test.1example.com`, `test.example.com2`).
* If the match prefix is not present, the pattern will match the exact domain only (i.e., `example.com` will match `example.com` and will not match `test.example.com`, `1example.com`, `example.com2`).

`email`
: The string value is an email address conforming to the syntax of [RFC 5322](https://www.rfc-editor.org/rfc/rfc5322.txt). e.g., `user@example.com`.

`hostname`
: The string value is a hostname, IPv4 address, or IPv6 address (with the IPV6 literal enclosed in square braces). e.g., `server.example.com`, `10.0.1.1`, `[fe80::1]`.

`localtime`
: The string value is a date and time conforming to the syntax of [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339.txt) without a `time-offset` or `time-secfrac` element: `YYYY-MM-DDTHH:MM:SS`. e.g., `2023-09-21T12:00:00`.

`regex`
: The string value is a regular expression.

`timestamp`
: The string value is a date and time conforming to the syntax of [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339.txt) with a `time-offset` element, and without a `time-secfrac` element: `YYYY-MM-DDTHH:MM:SSZ` or `YYYY-MM-DDTHH:MM:SS+ZZZZ`. e.g., `2023-09-21T12:00:00Z`, `2023-09-21T12:00:00-0500`.

`url`
: The string value is a URL conforming to the syntax of [RFC 3986](https://www.rfc-editor.org/rfc/rfc3986.txt).

`uuid`
: The string value is a 36-character UUID, with both lowercase and uppercase hexadecimal digits allowed.

### Range Object

| Name | Type            | Description |
|------|-----------------|-------------|
| min  | integer or real | Lower bound of range |
| max  | integer or real | Upper bound of range |

### Repetition Object

| Name | Type            | Description |
|------|-----------------|-------------|
| min  | integer or real | Lower bound of repetition |
| max  | integer or real | Upper bound of repetition |

## Schema Use

The schema has minor variants based on the nature of the object being described.

### MDM Commands/CheckIn

An MDM command or checkin is a YAML object with the following top-level keys:

| Name         | Type   | Description |
|--------------|--------|-------------|
| title        | string | Title for this schema object |
| description  | string | Description of this schema object |
| payload      | object | Information about the object as a whole |
| payloadkeys  | array  | A list of YAML objects representing the command request |
| responsekeys | array  | A list of YAML objects representing the command response |

The `payload` object will contain a `requesttype` key that specifies the command or CheckIn request name.

### MDM Profiles

An MDM profile is a YAML object with the following keys:

| Name         | Type   | Description |
|--------------|--------|-------------|
| title        | string | Title for this schema object |
| description  | string | Description of this schema object |
| payload      | object | Information about the object as a whole |
| payloadkeys  | array  | A list of YAML objects representing the profile keys |

The `payload` object will contain a `payloadtype` key that specifies the payload type.

### RM model declarations

An RM declaration is a YAML object with the following keys:

| Name         | Type   | Description |
|--------------|--------|-------------|
| title        | string | Title for this schema object |
| description  | string | Description of this schema object |
| payload      | object | Information about the object as a whole |
| payloadkeys  | array  | A list of YAML objects representing the declaration keys |

The `payload` object will contain a `declarationtype` key that specifies the declaration type.

### RM model status item

An RM status item is a YAML object with the following keys:

| Name         | Type   | Description |
|--------------|--------|-------------|
| title        | string | Title for this schema object |
| description  | string | Description of this schema object |
| payload      | object | Information about the object as a whole |
| payloadkeys  | array  | A list of YAML objects representing the status item key |

The `payload` object will contain a `statusitemtype` key that specifies the status item type. The `payloadkeys` will contain a single object that defines the type of the value returned for the status item.

### RM protocol

An RM protocol request or response is a YAML object with the following top-level keys:

| Name         | Type   | Description |
|--------------|--------|-------------|
| title        | string | Title for this schema object |
| description  | string | Description of this schema object |
| payload      | object | Information about the object as a whole |
| payloadkeys  | array  | A list of YAML objects representing the request or response |

The `payload` object will contain a `requesttype` key that specifies the summary description of the request or response.

## Subkey structure

A payload key can have a scalar type (`<string>`, `<integer>`, `<real>`, `<boolean>`, `<data>`) or a container type (`<array>`, `<dictionary>`). A container type must include a `subkeys` key that defines the details of the container as follows:

### `<dictionary>` container

The `subkeys` sequence in a `<dictionary>` container defines the schema for the dictionary contents.

### `<array>` container

The `subkeys` sequence in a `<array>` container defines the type of items in the array. Only a single item is allowed in the `subkeys` sequence. The type of the single item defines the structure of the container as follows:

* if the single item's type is a scalar type, then the array is a list of items with elements matching the scalar type (e.g. an array of `<string>` values). In some cases the scalar type may have a `subkeys` key, and each element of that sequence defines a possible value for the scalar type in the array.

* if the single item's type is `<dictionary>`, then the array is a list of dictionary items, with each dictionary conforming to the schema defined by the `subkeys` item of the single item (e.g., an array of `<dictionary>` values). Note that the single item `<dictionary>` is only a place holder for the keys used in the `<dictionary>` array items, and as such does not itself appear as the an array item.

* if the single item's type is `<array>`, then the array is a list of array items, with each array item conforming to the schema defined for an `<array>` container as described in this section.
