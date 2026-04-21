# Zyxel Nebula OpenAPI Release Note

**Version**: `0.1.34` → `0.1.36`

## Executive Summary

This release introduces significant enhancements across WLAN management and organization-level operations, focusing on flexibility and control.

- **Expanded WLAN Management**: New capabilities for granular control over AP WLAN settings, including schedules, rate limits, band modes, intra-BSS traffic, and captive portal customizations.
- **Enhanced Security**: Introduction of Dynamic Personal Pre-Shared Key (DPPSK) management for SSIDs.
- **Organizational License and Trial Management**: New endpoints to manage organization upgrades, device license registration, and trial status activation.
- **Data Model Updates**: The `Device` and `ValidationError` schemas have been updated with new fields to provide richer data.

## New Endpoints

### Tag: ap

These new endpoints provide comprehensive control over various AP WLAN settings, enabling more flexible and secure network configurations.

#### Get Wlan Schedules

- **Method**: `GET`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-schedule`
- **Description**: SSID schedule is a many-to-one relationship with SSID

#### Assign Wlan Schedules

- **Method**: `PATCH`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-schedule`
- **Description**: SSID schedule is bound with each SSID.

#### Create Wlan Schedule

- **Method**: `POST`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-schedule`
- **Description**: SSID schedule is bound with each SSID.

#### Update Wlan Schedule

- **Method**: `PUT`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-schedule/{scheduleId}`
- **Description**: Update Wlan Schedule

#### Delete Wlan Schedule

- **Method**: `DELETE`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-schedule/{scheduleId}`
- **Description**: SSID schedule is bound with each SSID.

#### Get Wlan Rate Limit

- **Method**: `GET`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-rate-limit`
- **Description**: Get the WLAN rate limit settings for all SSIDs.

#### Update Wlan Rate Limit

- **Method**: `PATCH`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-rate-limit`
- **Description**: Update WLAN rate limit settings for specified SSIDs.

#### Get Wlan Band Mode

- **Method**: `GET`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-band-mode`
- **Description**: Get the WLAN Band Mode settings for all SSIDs.

#### Update Wlan Band Mode

- **Method**: `PATCH`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-band-mode`
- **Description**: Update WLAN Band Mode settings for specified SSIDs.

#### Get Wlan Intra Bss Traffic

- **Method**: `GET`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-intra-bss-traffic`
- **Description**: Get the WLAN Intra BSS Traffic settings for all SSIDs.

#### Update Wlan Intra Bss Traffic

- **Method**: `PATCH`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-intra-bss-traffic`
- **Description**: Update WLAN Intra BSS Traffic settings for specified SSIDs.

#### Update Captive Portal Logo

- **Method**: `PATCH`
- **Path**: `/v1/nebula/{siteId}/ap/captive-portal-logo`
- **Description**: Update (or delete) the logo image for a specific captive portal SSID slot.

- `id`: SSID slot index (1-8)
- `logoBase64`: Base64-encoded image string to upload.
  Pass `null` to remove the existing logo.

#### Get Dppsk

- **Method**: `GET`
- **Path**: `/v1/nebula/{siteId}/ap/dppsk`
- **Description**: Get Dppsk

#### Create Dppsk

- **Method**: `POST`
- **Path**: `/v1/nebula/{siteId}/ap/dppsk`
- **Description**: Create Dppsk

#### Enable Dppsk On Ssid

- **Method**: `PATCH`
- **Path**: `/v1/nebula/{siteId}/ap/wlan-dppsk`
- **Description**: Enable DPPSK security mode on a specific SSID.
  Optionally sets the backup pre-shared key (wifi_preshared_key).

#### Get Ssid Grouping

- **Method**: `GET`
- **Path**: `/v1/nebula/{siteId}/ap/ssid-grouping`
- **Description**: Get the SSID Grouping status for the site.
  (This feature allows creating more than 8 SSIDs, also known as AP Grouping).

#### Update Ssid Grouping

- **Method**: `PUT`
- **Path**: `/v1/nebula/{siteId}/ap/ssid-grouping`
- **Description**: Update the SSID Grouping status for the site.
  (This feature allows creating more than 8 SSIDs, also known as AP Grouping).

### Tag: organizations

These new endpoints empower users to manage organization-level functions such as upgrading to PRO, registering device licenses, and overseeing trial statuses.

#### Upgrade Organization

- **Method**: `PATCH`
- **Path**: `/v1/nebula/organizations/{orgId}/upgrade-org`
- **Description**: - Upgrade an organization to PRO Level.
- No PRO organization status required for using this API.

#### Register Device License

- **Method**: `POST`
- **Path**: `/v1/nebula/organizations/{orgId}/device/{devId}/license`
- **Description**: - Register license to a device.
- No PRO organization status required for using this API.

#### Get Org Trial Status

- **Method**: `GET`
- **Path**: `/v1/nebula/organizations/{orgId}/trial/status`
- **Description**: - Get trial status for an organization.
- No PRO organization status required for using this API.

#### Activate Trial For Organization

- **Method**: `POST`
- **Path**: `/v1/nebula/organizations/{orgId}/trial/activate`
- **Description**: - Activate trial for an organization.
- No PRO organization status required for using this API.

## Schema Changes

### A. Device Schema

- `assetId`: Newly added field.
- **Affected Endpoints**: GET /v1/nebula/organizations/{orgId}/sites/devices
