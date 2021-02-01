# Development environment setup

You'll need the following software installed:

* Java 11
* Git
* IntelliJ IDEA Community Edition 2020.3.2 or newer

In order to start working on the lab practicals and eventually the coursework, your machine needs to
have **Java 11** installed.

**Do not install Java 8/9/10/12/13/14/15** -- we do not support it, and _you_ are responsible for solving
any issues you might encounter due to the Java version mismatch. If you have already installed an
incompatible version of Java, we recommend you remove it completely and install Java 11 instead.
Refer to [the Uninstall section](#uninstalling-other-java-versions) for some hints on how to do
this.

**Your Java installation must not be in WSL, and running Java or IntellJ inside a virtual machine is
not a supported configuration.**

## Lab machines (MVB 2.11 remote access only)

A fairly recent version Git is already installed. A copy of Java 11 should already be installed
at `/usr/lib/jvm/java-11`.

Run the following in a terminal:

```shell
export JAVA_HOME=/usr/lib/jvm/java-11
export PATH="$JAVA_HOME/bin:$PATH"
```

And then verify that Java works:

```shell
bash-4.2$ java -version
openjdk version "11.0.6" 2020-01-14 LTS
OpenJDK Runtime Environment 18.9 (build 11.0.6+10-LTS)
OpenJDK 64-Bit Server VM 18.9 (build 11.0.6+10-LTS, mixed mode, sharing)
```

Then append the two export commands to your `~/.bashrc` (or whatever shell you happen to be using),
for example, open the `~/.bashrc` file with

    code ~/.bashrc

Paste the two export commands at the very end of the file and then save. Close and reopen all
terminal windows for the change to take effect.

For IntelliJ, a slightly older version should already been installed:

* `Xfce` : `Applications` -> `Development` -> `IntelliJ IDEA 2019 CE`
  or `IntelliJ IDEA Community Edition`

If you can't find the app from the desktop environment, you can launch it from the terminal by
executing:

    /opt/idea/2019/bin/idea.sh

Once you have verified Java 11 and IntelliJ is working, the setup is complete.

## Installing on your own machine

### Windows

**Do not attempt to install Java, Git, or IntelliJ inside WSL or a virtual machine.**

**Keep in mind that WSL is a separate OS, we will be doing development directly on Windows, so you
will still need to install Git on Windows**

First, download Git for Windows [here](https://git-scm.com/download/win). Double click and follow
installation instructions, pick an editor you are familiar with in
the `Choosing the default editor used by Git` screen and *leave the rest of the screens default*.
Once installed, open a terminal by right clicking on the Windows `Start` button and
select `Windows PowerShell`(**Do NOT use WSL here**). In the PowerShell window, verify that Git
works:

```shell
PS C:\Users\YourUserName> git --version
git version 2.30.0.windows.2
```

Proceed to install Java 11 by downloading the x64 hotspot version of
AdoptOpenJDK [here](https://github.com/AdoptOpenJDK/openjdk11-binaries/releases/download/jdk-11.0.10%2B9/OpenJDK11U-jdk_x64_windows_hotspot_11.0.10_9.msi)
. Double click and follow installation instructions, *leave all settings default*.  
Once installed, verify that Java works in PowerShell:

```shell
PS C:\Users\YourUserName> java -version
openjdk version "11.0.10" 2021-01-19
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.10+9, mixed mode)
PS C:\Users\YourUserName> javac -version
javac 11.0.10
```

Proceed to install IntelliJ. Download [Jetbrains toolbox](https://www.jetbrains.com/toolbox-app/),
double-click on the exe and follow installation instructions, *leave all settings default*. Once
installed, it should appear in your system tray, click on the icon and accept the EULA, a product
list should appear. If it does not appear in the system tray, search for `JetBrains Toolbox` in the
start menu. Once you are at the product list, click `install` on
the  `IntelliJ IDEA Community Edition` entry.
`IntelliJ IDEA Community Edition` should be available in the start menu. Check that you can start
IntelliJ without issues.

### Linux

**This only applies to your *own* Linux setup that isn't a virtual machine, this is also not
recommended for the Lab machines**

Git should already be installed if you are one a sane Linux distro, if not, install through your distro's package manager:

* Fedora: `sudo dnf install git`
* Ubuntu/Debian: `sudo apt install git`

Likewise, install Java 11 in the same way, for example:

* Fedora: `sudo dnf install java-11-openjdk java-11-openjdk-jmods`
* Ubuntu/Debian: `sudo apt install openjdk-11-jdk`

Verify that Git and Java 11 has been installed correctly:

```shell
> git --version
git version 2.29.2
> java -version 
openjdk version "11.0.9.1" 2020-11-04
OpenJDK Runtime Environment 18.9 (build 11.0.9.1+11)
OpenJDK 64-Bit Server VM 18.9 (build 11.0.9.1+11, mixed mode, sharing)
> javac -version
javac 11.0.9.1
```

Proceed to install Jetbrains toolbox from the terminal.

First make sure `wget` is installed:
 * Fedora: `sudo dnf install wget`
 * Ubuntu/Debian: `sudo apt install wget`

Then, download and start the toolbox:
```shell
> wget https://download.jetbrains.com/toolbox/jetbrains-toolbox-1.19.7784.tar.gz
> tar -xf jetbrains-toolbox-1.19.7784.tar.gz
> ./jetbrains-toolbox-1.19.7784/jetbrains-toolbox
```




A product list window should appear shortly on the top right (it may take up to 1 minute on first
launch).

Once you are at the product list window, click `install` on the  `IntelliJ IDEA Community Edition`
entry.
`IntelliJ IDEA Community Edition` should be available in your window manager.

### macOS

Git is part of Xcode, it will install itself on first launch:

```shell
> git --version
xcode-select: note: no developer tools were found at ....
Choose an option in the dialog to download the command line developer tools.
```

Accept the agreements and proceed to install.

The recommended way to install Java 11 is to use [Homebrew](https://brew.sh/). You may already
have `brew` installed, run the following in the Terminal:

```shell
> brew --version
Homebrew 2.7.7
Homebrew/homebrew-core (git revision 60f25; last commit 2021-01-31)
Homebrew/homebrew-cask (git revision 27a13; last commit 2021-01-31)
```

If you don't see that output, proceed to install Homebrew:

```shell
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once `brew` installed, proceed to install Java 11:

```shell
> brew update # this may take anywhere from 10 to 30 minutes
> brew tap AdoptOpenJDK/openjdk
> brew cask install adoptopenjdk11
```

If you happen to be on macOS Catalina or newer, you may have to enable permissions for the Terminal.

Proceed to install IntelliJ. Download [Jetbrains toolbox](https://www.jetbrains.com/toolbox-app/).
Like installing any macOS app, open the DMG image and drag the app to the Application directory.
Once the app is copied, click on the icon and accept the EULA, a product list should appear. Search
for `JetBrains Toolbox` in Spotlight if you cannot locate the app. At the product list window,
click `install` on the  `IntelliJ IDEA Community Edition` entry.
`IntelliJ IDEA Community Edition` should be available in *Launchpad*. Check that you can start
IntelliJ without issues.

## Uninstalling other Java versions

The easiest way to make sure you're using the correct Java version (Java 11) is to not have any
other versions installed. If you _need_ other versions, then you should make sure that you use Java
11 for the coursework. If you use an IDE, there should be a setting allowing you to choose which JDK
you use, and on Linux you can use
[update-alternatives](https://linux.die.net/man/8/update-alternatives) (or
[update-java-alternatives on Ubuntu](https://askubuntu.com/questions/315646/update-java-alternatives-vs-update-alternatives-config-java))
.

To uninstall Java 8/9/10/12/13 (or other unsupported versions):

* On Windows, use the Control Panel.
* On Linux, use your package manager, e.g. `sudo apt remove openjdk-9-jdk`.
* On Mac, depending on how you installed Java:
    - Using Homebrew: `brew cask uninstall java`
    - Manually using a package downloaded from the Oracle website (note the version number in the
      first command, which you may need to change according to what you installed):

  ```shell
  sudo rm -rf /Library/Java/JavaVirtualMachines/jdk-9*.jdk/
  sudo rm -rf /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
  sudo rm -rf /Library/PreferencePanes/JavaControlPanel.prefPane
  ```

