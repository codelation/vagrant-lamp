# 81vagrants Virtual Environment

Vagrant virtual environment for use within 81designs for Wordpress sites.

### 1. Install Required Software

OS X Command Line Tools, VirtualBox, and Vagrant must be installed.

- **OS X Command Line Tools** - Install from Xcode
- **VirtualBox** - <http://www.virtualbox.org>
- **Vagrant** - <http://vagrantup.com>
    

### 2. Build Environment

Go to the repository folder and launch the build script.

    $ cd vagrant-lamp
    $ vagrant up
    
### 3. Add site files and configuration

Create [install directory]/data_bags/sample.json that contains

    `{
        "id": "sample",
        "host": "sample.dev",
        "aliases": [
            "www.sample.dev"
        ]
    }`
    
Add your project files to [install directory]/www/sample.dev

    
### 4. Edit Hosts File

Add to `/etc/hosts`:

    55.55.55.20    sample.dev www.sample.dev
    
### 5. Edit The Site

The site is now accessible by pointing your browser to <http://sample.dev> or <http://localhost:5520>.


##Access Installed Software

Webgrind and phpMyAdmin are available on every domain.

    phpMyAdmin - http://sample.dev/phpmyadmin
        User: root
        Password: vagrant
    Webgrind - http://sample.dev/webgrind

PHP is configured to send mail via MailCatcher. The web frontend for MailCatcher is running on port 1080 and also available on every domain:

    MailCatcher - http://sample.dev:1080

