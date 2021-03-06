RCMCardDAV
==========

CardDAV plugin for the RoundCube Webmailer

Upgrading from 1.0
==================

There is no upgrade path from the 1.0 version. You need to manually remove RCMCardDAV 1.0, drop its tables from your database and start with a fresh installation.

Installation
============

RCMCardDAV can be installed via composer, from a release tarball or from a git clone. This list is in increasing difficulty, with composer being the easiest method.

Please note that due to version incompatibilities of depending libraries, this plugin might be incompatible to Kolabs calendar plugin. There is a compatible version available here: `http://git.faster-it.de/roundcube_calendar/`.

Intallation steps:
- Log out of Roundcube!
  This is important because RCMCardDAV runs its database initialisation / update procedure only when a user logs in!
- Get RCMCardDAV
  - Via composer:
    - Add `"roundcube/carddav": "dev-master"` to your composer.json file and install with `php composer.phar install`.
  - Via git:
    - Clone the repository:
      `cd roundcube/plugins && git clone git@github.com:blind-coder/rcmcarddav.git carddav`
    - Install dependencies:
      - Install composer as per the documentation: https://getcomposer.org/download/
      - Run `php composer.phar install`
  - Via release tarball:
    - Download and extract the release tarball into `roundcube/plugins` directory and rename the extracted directory to `carddav`. The tarball contains all necessary dependencies and does not need composer.
- Configure RCMCardDAV
  If you want to configure preset addressbooks for your users, copy the file `config.inc.php.dist` to `config.inc.php` and edit it as you need.
- Make sure that the files and directories are owned by the user and group that your webserver runs as. For Debian GNU/Linux that would be:
  `chown -R www-data:www-data roundcubemail/plugins/carddav`
- Install the curl php extension if not already present:
  `sudo apt-get install php5-curl`
- Enable RCMCardDAV in Roundcube:
  Open the file `roundcubemail/config/main.inc.php` and add `carddav` to the array `$rcmail_config['plugins']`.
- Login to Roundcube and setup your addressbook by navigation to the Settings page and click on CardDAV.

In case of errors, check the files `roundcube/logs/*`.
