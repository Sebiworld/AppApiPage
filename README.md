AppApiPage adds the /page endpoint to the [AppApi](https://modules.processwire.com/modules/app-api/) routes definition. Makes it possible to query pages via the api.

[![Current Version](https://img.shields.io/github/v/tag/Sebiworld/AppApiPage?label=Current%20Version)](https://img.shields.io/github/v/tag/Sebiworld/AppApiPage?label=Current%20Version) [![Current Version](https://img.shields.io/github/issues-closed-raw/Sebiworld/AppApiPage?color=%2356d364)](https://img.shields.io/github/issues-closed-raw/Sebiworld/AppApiPage?color=%2356d364) [![Current Version](https://img.shields.io/github/issues-raw/Sebiworld/AppApiPage)](https://img.shields.io/github/issues-raw/Sebiworld/AppApiPage)

<a href="https://www.buymeacoffee.com/Sebi.dev" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

| | |
| ------------------: | -------------------------------------------------------------------------- |
| ProcessWire-Module: | [https://modules.processwire.com/modules/app-api-page/](https://modules.processwire.com/modules/app-api-page/)                                                                    |
|      Support-Forum: | [https://processwire.com/talk/topic/26855-appapi-module-appapipage/](https://processwire.com/talk/topic/26855-appapi-module-appapipage/)                                                                      |
|         Repository: | [https://github.com/Sebiworld/AppApiPage](https://github.com/Sebiworld/AppApiPage) |

Relies on AppApi:

| | |
| ------------------: | -------------------------------------------------------------------------- |
| AppApi-Module: | [https://modules.processwire.com/modules/app-api/](https://modules.processwire.com/modules/app-api/)                                                                    |
|      Support-Forum: | [https://processwire.com/talk/topic/24014-new-module-appapi/](https://processwire.com/talk/topic/24014-new-module-appapi/)                                                                      |
|         Repository: | [https://github.com/Sebiworld/AppApi](https://github.com/Sebiworld/AppApi) |
| AppApi Wiki: | [https://github.com/Sebiworld/AppApi/wiki](https://github.com/Sebiworld/AppApi/wiki) |
| | |

<a name="installation"></a>

## Installation

AppApiPage relies on the base module AppApi, which must be installed before AppApiPage can do its work.

AppApi and AppApiPage can be installed like every other module in ProcessWire. Check the following guide for detailed information: [How-To Install or Uninstall Modules](http://modules.processwire.com/install-uninstall/)

The prerequisites are **PHP>=7.2.0** and a **ProcessWire version >=3.93.0** (+ **AppApi>=1.2.0**). However, this is also checked during the installation of the module. No further dependencies.

<a name="quickstart"></a>

## Quickstart

AppApiPage will add an api-endpoint that can be used to call any page in the processwire pagetree.

| Route         | Description |
| ------------- | -------- |
| **/api/page/** | Calls the root page of the page-tree |
| **/api/page/42** | Will call the page with id=`42` |
| **/api/page/my/test/page** | Calls your page with path `my/test/page` |

Simply add the following code at the top of your ProcessWire-template to add JSON output:

```php
<?php
// Check if AppApi is available:
if (wire('modules')->isInstalled('AppApi')) {
  $module = $this->wire('modules')->get('AppApi');
  // Check if page was called via AppApi
  if($module->isApiCall()){
    // Output id & name of current page
    $output = [
      'id' => wire('page')->id,
      'name' => wire('page')->name
    ];

    // sendResponse will automatically convert $output to a JSON-string:
    AppApi::sendResponse(200, $output);
  }
}

// Here continue with your HTML-output logic...
```

<a name="changelog"></a>

## Changelog

### Changes in 1.0.2 (2022-06-01)

- Bugfix throw 404 status if not found

### Changes in 1.0.1 (2022-04-29)

- Added support for Multi-Language URLS

### Changes in 1.0.0 (2022-03-06)

- Added page endpoint

<a name="versioning"></a>

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/Sebiworld/AppApiPage/tags).

<a name="license"></a>

## License

This project is licensed under the Mozilla Public License Version 2.0 - see the [LICENSE.md](LICENSE.md) file for details.
