# kick-off

Scripts used in the process of a Docker image build and/or used to trigger processes in a Docker container.

## Description

Utility used as helper in the process of building parts of a Docker image, plus configurator to trigger processes
when a container is launched, plus services daemon launcher, plus signal processor to communicate with such processes.

This was created in order to have a common structure to use when processing building pieces for a Docker image. 
Later, the objective became broader, as it now is used to deploy processes run by the container too, and respond
to signals. It's the replacement for supervisor.

In the case of the folder structure, this command aims for something as defined in the example folder shown in this
repo. Please, check that for deeper information.

## Folder Structure

It's really simple, aimed to enable program distribution under different formats. 

- ***src***: contains all the real code on the solution.
- ***snap***: configurations to create a snap package on the project.
- ***Makefile***: configurations to install the package but using the ubiquitous make tool.
- ***example***: boilerplate to be used when a process config/run step is required.

## Source Code Explanation

Next an explanation of each file here defined:

* `src/usr/bin/kick-off`: Command aimed to perform all the operations. Behavior is controlled by parameters passed.
as shown before.

# Makefile

Clone the project and, inside of it, run:

```
sudo make install
```

Done! For upgrades, simply clone the project again and run the previous command again.

To remove simply run `sudo make uninstall`.

# Snap Package

Check **snap** folder with all configuration information ready to build a snap package. More info about snaps here https://docs.snapcraft.io/snaps/intro.

Commands to trigger package creation can be run from this project's root level.

## TODO:
- Check how to create a cleaner snap package. So far, when run `snapcraft cleanbuild` command, everything goes great, but there's a .bz2 file inside the created snap that has everything this repo has, even **.git** folder, and that's how that's published. No Bueno!
