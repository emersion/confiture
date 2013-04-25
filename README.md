confiture 1.0 alpha 1
=====================

A simple package control system specification, designed for the web, based on JSON and ZIP.

Repository structure
=================

* / - repository directroy
* /packages/ - packages directories
* /index.json - contains a list of all packages available
* /metadata.json - contains metadata about the repository

packages/
---------

Packages directories are located in sub-directories entitled with their first letter. For exemple, the package _yaourt_ would be located in _packages/y/yaourt/_.

index.json
----------

This file is a list of each package's metadata.

metadata.json
-------------

This file contains metadata about the repository (e.g. its title, maintainer). Its kind is the platform on which packages can be installed. The _specification_ field is the confiture specification version.
```json
{
  "title":"Lighp official repository",
	"kind":"lighp",
	"specification":"1.0",
	"maintainer":"Simon Ser"
}
```

Package structure
=================

Each package in the repository has its own directory, which contains :
* source.zip : the package's source
* metadata.json : the package's metadata
* files.json : the package's files

source.zip
----------

This is a ZIP file with 1 folder named _src_, which corresponds to the platform's root folder.

Additionnaly, it can contain **INSTALL._xxx_** and **REMOVE._xxx_** files, which will be executed after installation and before uninstallation.

metadata.json
-------------

This file contains metadata about the package :
* **name** : the package's name. Must contain only alphabetical characters and _-_.
* **title** : the package's title
* **subtitle** : a one-line description of the package
* **description** : a complete description of the package
* **version** : the package's version
* **url** : the package's website
* **license** : the package's license
* **maintainer** : the name of the package's maintainer
* **updateDate** : the package's last update date. Must be in MySQL-format (i.e. `YYYY-MM-DD HH-MM-SS`).
* **size" : the _source.zip_ file size
* **extractedSize** : the package's size, when extracted
* **hasScripts** : determines if the package has install/uninstall scripts

```json
{
    "hasScripts": false, 
    "subtitle": "Core files for Lighp", 
    "description": "A light-weight php framework based on a package system.", 
    "license": "GPLv3", 
    "title": "lighp-core", 
    "url": "http://github.com/lighp/lighp", 
    "version": "1.0alpha1", 
    "updateDate": "2013-04-19 08:18:46", 
    "maintainer": "Simon Ser", 
    "size": 96106, 
    "extractedSize": 232105, 
    "name": "lighp-core"
}
```

files.json
----------

Contains a list of the package's files, with their checksums.

```json
{
  "/CHANGELOG.md":{"md5sum":"fe295cebe9c15603045ed64cc78a4df8"},
	"/COPYING":{"md5sum":"d32239bcb673463ab874e80d47fae504"},
	"/core/ApiBackController.class.php":{"md5sum":"4c22f3f06bc07de1c47e12d9948f0e84"},
	"/core/ApiResponse.class.php":{"md5sum":"542732e0c5044dfa33b5139a904798fa"},
  ...
}
```
