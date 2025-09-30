+++
date = '2025-09-30T23:58:18+05:30'
title = 'Remove Ubuntu Snap'
tags= ['linux', 'guide']
+++
This guide shows you how to remove snap packages from an Ubuntu System
> Remember to install a browser before removing snaps on a Ubuntu System.

1. View all snaps

    ```sh
    snap list
    ```

1. Remove snap packages in the following order. Firstly remove Firefox. Secondly, snap-store and the other packages that you see in the above command output in your system.

    ```sh
    sudo snap remove --purge firefox
    sudo snap remove --purge snap-store
    sudo snap remove --purge gnome-*
    ```

    ```sh
    sudo snap remove --purge gtk-common-themes
    sudo snap remove --purge snapd-desktop-integration
    sudo snap remove --purge bare
    sudo snap remove --purge core*
    sudo snap remove --purge snapd
    ```
1. Finally, remove the snap daemon via apt command.

    ```sh
    sudo apt remove --autoremove snapd
    sudo nala --autoremove
    ```
1. So, to stop that, we need to create an apt preference file in `/etc/apt/preferences.d` and create a new preference file to stop snap. 

    ```sh
    sudo -H gedit /etc/apt/preferences.d/nosnap.pref
    ```
1. And add the following lines, then save the file.

    ```sh
    Package: snapd
    Pin: release a=*
    Pin-Priority: -10
    ```
1. Returning to the topic, once you save and close the above file, run the below again from the terminal.

    ```sh
    sudo nala update
    ```

> Refrence: [Source](https://www.debugpoint.com/remove-snap-ubuntu/)