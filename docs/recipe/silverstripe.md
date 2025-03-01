<!-- DO NOT EDIT THIS FILE! -->
<!-- Instead edit recipe/silverstripe.php -->
<!-- Then run bin/docgen -->

# How to Deploy Silverstripe

[Source](/recipe/silverstripe.php)

## How to deploy a Silverstripe project with zero downtime?

- First, [install](/docs/installation.md) the Deployer. 
- Second, require `recipe/silverstripe.php` recipe into your _deploy.php_ or _deploy.yaml_ file.
- Third, and now you can have a zero downtime deployment!

Did you know that you can deploy **Silverstripe** project with a single command? Just execute `dep deploy`.
Something went wrong? Just run `dep rollback` to rollback your changes.
Also, you can take an advantages of the [Deployer's CLI](/docs/cli.md) to deploy your project.

Also, another feature of the Deployer is [provisioning](/docs/recipe/provision.md). Take any server, and run `dep provision` command.
This command will configure webserver, databases, php, https, and more. 
You will get everything you need to run your **Silverstripe** project.

Deployer does next steps to [deploy](#deploy) **Silverstripe**:
* Displays info about deployment
* Prepares host for deploy
* Locks deploy
* Prepares release
* Updates code
* Creates symlinks for shared files and dirs
* Makes writable dirs
* Installs vendors
* Runs /dev/build?flush=all
* Creates symlink to release
* Unlocks deploy
* Cleanup old releases


The silverstripe recipe is based on the [common](/docs/recipe/common.md) recipe.

## Configuration
### shared_assets
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L12)





### shared_dirs
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L21)

Overrides [shared_dirs](/docs/recipe/deploy/shared.md#shared_dirs) from `recipe/deploy/shared.php`.

Silverstripe shared dirs

```php title="Default value"
[
    '{{shared_assets}}'
]
```


### writable_dirs
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L26)

Overrides [writable_dirs](/docs/recipe/deploy/writable.md#writable_dirs) from `recipe/deploy/writable.php`.

Silverstripe writable dirs

```php title="Default value"
[
    '{{shared_assets}}'
]
```


### silverstripe_cli_script
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L31)

Silverstripe cli script




## Tasks

### silverstripe:build
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L47)

Runs /dev/build.

Helper tasks


### silverstripe:buildflush
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L52)

Runs /dev/build?flush=all.




### deploy
[Source](https://github.com/deployphp/deployer/blob/master/recipe/silverstripe.php#L60)

Deploys your project.

Main task


This task is group task which contains next tasks:
* [deploy:prepare](/docs/recipe/common.md#deployprepare)
* [deploy:vendors](/docs/recipe/deploy/vendors.md#deployvendors)
* [silverstripe:buildflush](/docs/recipe/silverstripe.md#silverstripebuildflush)
* [deploy:publish](/docs/recipe/common.md#deploypublish)


