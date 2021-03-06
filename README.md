# AlCapON : Enable Capistrano for your eZ Publish installations

AlCapON is a simple recipe for Capistrano, the well-known deployment toolbox.
It helps you dealing with simple task such as pushing your code to your
webserver(s), clearing cache, etc.

IMPORTANT: this package is currently under development, please consider testing
it on a preproduction environment before going further. Please also do read the
"Known bugs" section carefully.

CAPISTRANO dependency : we recommand not to use Capistrano >= 2.15 which for some
reason broke something (see https://github.com/alafon/alcapon/issues/7 and https://github.com/alafon/capistrano/commit/e4f207b4b44e9fa5fa18ec4e85a7469d94570095)

AlCapON is not fully compatible with Capistrano 3.x, we are working on it and we recommand to stay on the 2.x branch

## Changelog

### 0.4.x

 - removed in 0.4.15 : the 'ezpublish:var:link' task does not call `chown`
   anymore since we must not alter the permissions in shared ressources. They
   must be controlled by ezpublish ONLY
 - added in 0.4.1 : downloaded files are hashed so that they can be downloaded
   somewhere there's no eZ Publish installed
 - added eZ Publish 5.x support for ezpublish_legacy. This means that version
   of eZ Publish must be known by alcapon. You can either set ezpublish_version
   (accepted values are 4 or 5) in your Capfile or add `-S ezpublish_version=4`
   or `-S ezpublish_version=5` after your command line call, like this :
   cap production deploy -S ezpublish_version=5

### 0.3.x

 - added the possibility to trigger rename and in-file replace operations
   during the deployment (see the generated file
   config/deploy/production.rb after running the capezit command)

 - major changes in permissions management for the var/ folders. Previous
   versions tried to manage different cases by using sudo commands but I'm
   convinced that it is not the right place to do that. Permissions have to be
   handled by sysadmin, not Capistrano.
   This will be improved, maybe simplified again, in next versions.
   In consequence, you might experienced some issues, but please, let me know.

 - usage of siteaccess_list in ezpublish.rb is deprecated as of 0.3.0. Please
   use storage_directories instead (see issue #2)

## Requirements, installation & co

Please see [alafon.github.com/alcapon](http://alafon.github.com/alcapon)
