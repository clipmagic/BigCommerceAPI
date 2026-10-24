# BigCommerceAPI for ProcessWire

Connect a ProcessWire site to a BigCommerce store using the BigCommerce v3 PHP client.

The module stores the connection settings in ProcessWire and provides a configured API client for your templates and modules. What you build with that connection is up to you: for example, showing products from a BigCommerce catalogue on a ProcessWire site.

## Requirements

- ProcessWire 3.x and PHP 7.0 or newer, as declared by the module.
- PHP cURL, JSON and mbstring extensions, required by the bundled client.
- A BigCommerce API account with access to the resources you intend to use.

These are the declared minimum requirements, not a compatibility test matrix for current PHP or ProcessWire releases.

## Installation

The repository includes `vendor/` and its autoloader. Users do not need Composer or a separate dependency-install step.

1. Download the repository ZIP from GitHub, or use ProcessWire's module installer with the ZIP URL:

   ```text
   https://github.com/clipmagic/BigCommerceAPI/archive/refs/heads/master.zip
   ```

2. If installing manually, extract the files into `/site/modules/BigCommerceAPI/`. The `BigCommerceAPI.module` file and `vendor/` directory should sit directly inside that folder.
3. In ProcessWire, refresh the module list and install **BigCommerce V3 PHP API**.
4. Open the module settings and save your BigCommerce connection details.

The complete ZIP is also suitable for the ProcessWire Modules Directory download mechanism when its listing points to this version. A fresh-install test and any directory-listing update are separate release tasks.

## Connection settings

Enter the **Client ID**, **access token** and **store hash** for the BigCommerce store you want to use. `connect()` uses those three settings.

The configuration screen also contains a client-secret field. The current `connect()` method does not use it or implement an OAuth installation flow.

Use API permissions appropriate to your work. A catalogue display normally needs read access; writing to a store needs the corresponding write permissions. Keep credentials in the module settings, not in templates or the repository.

## Usage

Load the module and ask it for a client:

```php
$bc = $modules->get('BigCommerceAPI');
$client = $bc->connect();
```

For example, the bundled catalogue API can request products:

```php
$catalog = new \BigCommerce\Api\v3\Api\CatalogApi($client);
$response = $catalog->getProducts(['limit' => 10]);
$products = $response->getData();
```

The example shows the bundled client's method signatures; it has not been run against a store as part of this documentation update. Handle API errors in your application and paginate requests when retrieving a full catalogue.

See the [bundled client documentation](vendor/moderntribe/bigcommerce-api-php-v3/docs/client.md) for its usage notes and the [catalogue example](vendor/moderntribe/bigcommerce-api-php-v3/docs/examples/catalog-get-products.md). The bundled client is a snapshot of the API, so check [current BigCommerce documentation](https://docs.bigcommerce.com/) before relying on newer endpoints or features.

## Upgrading from the original version

Version 0.0.1 used the v2 PHP client. The current module source is version 0.0.3 and uses the v3 client through `connect()`.

The old `api()` helper remains in the module but still references the previous v2 client class. It is not a working v3 interface. Existing calls such as `$bc->api('getProduct', 125)` need to be adapted to the appropriate v3 API class and method.

`connect()` targets `/v3`. Resources that still use v2, including Customer Groups, need a separate v2 request; they are not provided through this v3 connection.

## Development and releases

Composer is used by maintainers to manage the bundled dependency. Keep `composer.json`, `composer.lock` and the required `vendor/` files together when updating it. Retain third-party licence and copyright notices.

Before tagging a release, test the GitHub-generated ZIP on a clean ProcessWire installation. Check installation, saved settings, authentication and an actual API request. Installing the files alone does not establish that the connection works.

See [CHANGELOG.md](CHANGELOG.md) for the recorded changes.

## Licence

The Clip Magic wrapper is licensed under the [MIT licence](LICENSE).

The bundled `moderntribe/bigcommerce-api-php-v3` client declares the Apache License 2.0. Its source notices remain intact; a copy of that licence is included in [licenses/Apache-2.0.txt](licenses/Apache-2.0.txt). Composer's bundled autoloader has its own [MIT licence](vendor/composer/LICENSE). These dependencies retain their respective licences.
