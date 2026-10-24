# Changelog

## Unreleased

- Added this changelog and a README covering installation, configuration and v3 usage.
- Added an MIT licence for the Clip Magic wrapper and aligned its source header.
- Added an Apache 2.0 licence copy for the bundled API client; retained dependency notices.
- Documented the legacy v2 `api()` helper limitation. No API behaviour was changed by this documentation update.

## 0.0.3 — current module source

The v3 update was developed in 2022 and added to this repository in October 2026. This heading records the module's declared version; it does not claim a published 0.0.3 release.

- Replaced the original v2 library with `moderntribe/bigcommerce-api-php-v3` (bundled version 2.3.3).
- Added `connect()` to create a v3 API client using saved Client ID, access token and store hash settings.
- Added a client-secret configuration field; the connection method does not use it.
- Bundled Composer dependencies in the repository for installation without a Composer step.
- Declared ProcessWire 3.0+ and PHP 7.0+ requirements.

The original `api()` helper still references the former v2 client class. Callers need to use the v3 client's API classes with `connect()`.

## 0.0.1 — original version

- ProcessWire wrapper around the BigCommerce v2 PHP client.
- Supported legacy BasicAuth and OAuth connection settings.
- Exposed the client through the module's `api()` helper.

The original version is preserved under the repository's `0.0.1` tag.
