# Installing Gekko on Mac

*NOTE: unfortunately installing and managing Gekko is hard. You will need to touch the commandline and install a few developer tools. I am creating an official Gekko service called [Gekko Plus](https://gekkoplus.com/) that will NOT require any installation.*

Here is a video of me explaining how to install Gekko the easiest way possible:

[![screen shot 2017-04-20 at 00 03 45](https://cloud.githubusercontent.com/assets/969743/25205894/e7f4ea64-255c-11e7-891b-28c080a9fbf2.png)](https://www.youtube.com/watch?v=R68IwVujju8)


To get Gekko running you need to do the following:

- set rights on your machine so that you have write rights for the gekko folder and all subsequent folders
- set energy saver preferences on your mac accordingly
- install nodejs
- install git
- download Gekko
- install Gekko & Gekko Broker dependencies

## Installing nodejs

Gekko requires [nodejs](https://nodejs.org/en/) to be installed. Go ahead and install this if it's not already (Gekko requires at least version 6). We advice to download the current LTS.

## Installing git

As part of Gekko's installation process git is used, see [this guide](https://www.linode.com/docs/development/version-control/how-to-install-git-on-linux-mac-and-windows/) for installation instructions. If you do not already have git on your system.

## Downloading Gekko

The recommended way of downloading Gekko is by using git. This makes keeping Gekko up to date a lot easier. Run this in a terminal:

    git clone git://github.com/askmike/gekko.git -b stable
    cd gekko

This will download the latest stable version of Gekko, remove the final `-b stable` part to download the current latest release (which might not be as stable).

Alternatively you can manually download the latest stable version of Gekko on the [releases page](https://github.com/askmike/gekko/releases).

## Set file permissions for the Gekko folder and all subsequent folders

Once you have Gekko downloaded you need to navigate to the gekko folder and make sure that file permissions are set correctly for the Gekko tree. You can do this via terminal:

    sudo chmod -R 777 ~/gekko

This will take care of the gekko folder and all subsequent folders.

## Installing Gekko's dependencies

Once you have Gekko downloaded you need to install the dependencies, open your terminal and navigate to the gekko folder and run:

    npm install --only=production

We also need to install Gekko Broker's dependencies, run:

    cd exchange
    npm install --only=production

## Starting Gekko

After all the above you can start Gekko by running the following in your terminal:

    node gekko --ui

## Updating Gekko

See the [updating Gekko](./updating_gekko.md) doc.
