# Development environment setup

In order to start working on the lab practicals and eventually the coursework,
your machine needs to have **Java 11** installed. **Do not install Java
8/9/10/12/13** -- we do not support it, and _you_ are responsible for solving any issues
you might encounter due to the Java version mismatch.

If you have already installed an incompatible version of Java, we recommend you remove it completely and
install Java 11 instead. Refer to [the Uninstall section](#uninstalling-other-java-versions)
for some hints on how to do this.

## Lab machines (MVB 2.11 only)

A copy of Java 11 should already be installed at `/usr/lib/jvm/java-11`.

Run the following in a terminal:

    export JAVA_HOME=/usr/lib/jvm/java-11
    export PATH="$JAVA_HOME/bin:$PATH"

And then verify that Java works:

    bash-4.2$ java -version
    openjdk version "11.0.6" 2020-01-14 LTS
    OpenJDK Runtime Environment 18.9 (build 11.0.6+10-LTS)
    OpenJDK 64-Bit Server VM 18.9 (build 11.0.6+10-LTS, mixed mode, sharing)

Then append the two export commands to your `~/.bashrc` (or whatever shell you have setup), for example, open the `~/.bashrc` file with 

    code ~/.bashrc

And the append the two export lines at the very end of the file and save. Close and reopen all terminal windows for the change to take effect.





## Installing on your own machine

### Windows

Download the latest **JDK** from
[AdoptOpenJDK](https://adoptopenjdk.net/installation.html?variant=openjdk11&jvmVariant=hotspot#x64_win-jdk), and follow the installation instructions [here](https://adoptopenjdk.net/installation.html?variant=openjdk11&jvmVariant=hotspot#x64_win-jdk).


### Linux

**IMPORTANT**

Ubuntu 18.04 LTS has a broken Java 11 package that are actually Java 10. do not install those! Follow the guide [here](https://www.linuxuprising.com/2018/10/how-to-install-oracle-java-11-in-ubuntu.html) to install the Oracle Java 11 package.   
<del>
Ubuntu's package repositories contain an up-to-date OpenJDK with latest
JavaFX jar as a separate package.
</del>

 1. <del>Update apt by typing `sudo apt update`</dev>
 2. <del>Install OpenJDK by typing `sudo apt install openjdk-11-jdk`</del>

Other Linux distribution should have similar packages, which you can obtain
through the corresponding package manager.

Make sure you remove any other Java versions you have installed.

### macOS / OS X

Download the latest **JDK** from
[here](https://adoptopenjdk.net/releases.html?variant=openjdk11&jvmVariant=hotspot#x64_mac) and follow the installation instructions [here](https://adoptopenjdk.net/installation.html?variant=openjdk11&jvmVariant=hotspot#x64_mac-jdk).

Alternatively, if you use [Homebrew](https://brew.sh/)<sup>†</sup>:

    brew tap caskroom/versions
    brew cask install java11

See [this Stack Overflow
question](https://stackoverflow.com/questions/52524112/how-do-i-install-java-on-mac-osx-allowing-version-switching)
for more information.

If you happen to be on macOS Catalina, you may have to enable permissions for the Terminal.

**†**: If you use a Mac and you're not already using Homebrew, you're missing
out on what of the best package managers out there. Brew is very easy to
install, use, and even remove if you need to, and it will simplify most (if not
all) package management that you will ever need to do on Mac. Refer to the
homepage for instructions or [the detailed docs
page](https://docs.brew.sh/Installation.html). Brew is so good that it has beed
[ported to Linux](http://linuxbrew.sh/) too!


----

You may have to set `JAVA_HOME` and add Java to `PATH` manually.

Korn and bash shells:

    export JAVA_HOME=jdk-install-dir
    export PATH=$JAVA_HOME/bin:$PATH

Bourne shell:

    JAVA_HOME=jdk-install-dir
    export JAVA_HOME
    PATH=$JAVA_HOME/bin:$PATH
    export PATH

C shell:

    setenv JAVA_HOME jdk-install-dir
    setenv PATH $JAVA_HOME/bin:$PATH
    export PATH=$JAVA_HOME/bin:$PATH

Confirm the installation by typing `java -version` and `echo $JAVA_HOME`.

## Uninstalling other Java versions

The easiest way to make sure you're using the correct Java version (Java 11) is
to not have any other versions installed. If you _need_ other versions, then you
should make sure that you use Java 11 for the coursework. If you use an IDE,
there should be a setting allowing you to choose which JDK you use, and on Linux
you can use
[update-alternatives](https://linux.die.net/man/8/update-alternatives) (or
[update-java-alternatives on Ubuntu](https://askubuntu.com/questions/315646/update-java-alternatives-vs-update-alternatives-config-java)).

To uninstall Java 8/9/10/12/13 (or other unsupported versions):

* On Windows, use the Control Panel.
* On Linux, use your package manager, e.g. `apt remove openjdk-9-jdk`.
* On Mac, depending on how you installed Java:
  - Using Homebrew: `brew cask uninstall java`
  - Manually using a package downloaded from the Oracle website (note the
  version number in the first command, which you may need to change according to
  what you installed):

  ```
  sudo rm -rf /Library/Java/JavaVirtualMachines/jdk-9*.jdk/
  sudo rm -rf /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
  sudo rm -rf /Library/PreferencePanes/JavaControlPanel.prefPane
  ```

