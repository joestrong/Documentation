title: Upgrade Guide
subtitle: Core module
-------

- [From v1 to v2](#upgrade-2.0)


## <a name="upgrade-2.0" class="anchor" href="#upgrade-2.0">From v1 to **v2**</a>

**Re-problish configuration files**

Configuration files across modules has been changed, mostly the `permissions.php` files.

Using the following command you will be able to publish a module config files.

``` .language-bash
php artisan module:publish-config --force
```

If you edited the module configurations, you will need to manually copy over the new files, depending on what you changed, you can also publish each module individually.

**Each module needs to handle config file loading**

Previously the Core module did the configuration loading for every module. This responsability has now been moved to every individual module. The reason is to have more flexibility on publishing modules configuration.

To register your configuration files, you can use a helper trait `CanPublishConfiguration`, with the `publishConfig($moduleName, $filename)` method. It takes the module name as first argument and the filename without extension as second.
