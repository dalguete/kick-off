This is an example of the folder structure this command expects in order to process things.

Next an explanation on different parts here defined:

* **init.sh** script, is the file in charge of triggering all necessary to correctly setup
the process wanted. If tasks become complicated, it's recommended to use the *scripts/* folder
to avoid having a too complex init script. There's some boilerplate code in this example script
that can be used for customizations.

* **configs/** is a folder that can be used to contain configuration files used in when a process
is installed in the image or when that's running. It's like a DB, nothing should be directly processed
here.

* **scripts/** is a folder that holds other scripts used when data processing in init.sh becomes
too complex. Avoid having a too long init.sh script, and instead distribute load among several
scripts here defined. Organization here is not attached to any paradigm, so good judge is called.
Don't forget, configuration live in the *configs/* folder, not in subfolder here defined.

* **daemon/** is a folder that holds scripts than will be used to trigger the daemon process when the
container is running. Despite the fact items here are scripts like the ones under *scripts/* folder,
these are aimed to be run when the container is running, so it's better to have them separated.

**IMPORTANT:** Alteration points must be offered by these scripts so other scripts can do extra
configuration/work before the daemon is triggered. This is desired as there is a lot of cases when
a given process requires some tune-up before it's launched, and having a different image for such
a thing is considered overkill. 

There's no standard and proper way to alter processes behavior and will be completely up to 
those processes themselves (so it's important to check each process documentation), but it's
encouraged for process makers to offer ways to alter this in a hookable fashion, like in the
example mentioned below:

* Process A can offer a way to alter settings before it runs by implementing a hook, like "init"
  for example. Process will start searching and executing every script found in
  /usr/local/share/kick-off/<process name>/<hook name>/. It's advised to execute executable files found,
  one by one, following lexicographical order, for instance, a **00-enable-debug.sh** can be run,
  to perform custom changes.

