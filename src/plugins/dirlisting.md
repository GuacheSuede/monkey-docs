# Directory Listing

The Directory Listing plugin allows to render the content of a directory in a friendly HTML interface when an index file do not exists. Take as an example the following Virtual Host directory content:

```
  /var/www/example/
                  /bar.zip
                  /foo.tar.gz
                  /sample.txt
```

When hitting the __example__ directory through the __http://localhost/example/__ URL, the server will try to lookup an index file, as described in the [Server Core](../configuration/server.md) section, the __IndexFile__ key defines which files can be an __index__, a few examples would be:

* index.html
* index.htm
* index.php

If one of the entries on the __IndexFile__ exists, the server will modify the target path __/var/www/example/__ and append the right index file. If no one exists, the server will return a __403 Forbidden__ HTTP error code.

## Enable Plugin

To enable the __Directory Listing__ plugin, please follow the steps mentioned on [Plugins](../configuration/plugins.md) section. The plugin name is __monkey-dirlisting.so__, so make sure the plugin entry is __Load__ and the absolute path is correct.

## Configuring

Once the plugin is loaded, you need to define which __Theme__ the plugin will use to render the directory content in HTML. At the moment the only __Theme__ available is called __Guineo__.

The main configuration file resides in __conf/plugins/dirlisting/dirlisting.conf__, and it contain the following schema:

```Python
[DIRLISTING]
    Theme guineo
```
The principal section is __[DIRLISTING]__ and allows just one key called __Theme__ to specify which theme should be loaded. The theme directory must exists in the same path than __dirlisting.conf__ exists.