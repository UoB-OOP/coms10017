# Development environment setup

In order to start working on the cw-model and cw-ai coursework,
your machine needs to have Java 11 installed. **Do not install Java
8/9/10** -- we do not support it, and _you_ are responsible for solving any issues
you might encounter due to the Java version mismatch.

If you have already installed Java 8/9/10, we recommend you remove it completely and
install Java 11 instead. Refer to [the Uninstall section](#uninstalling-other-java-versions)
for some hints on how to do this.


## Installing Java 11

### Windows


**For your own Windows machine:**

Download the latest JDK from
[AdoptOpenJDK](https://adoptopenjdk.net/installation.html?variant=openjdk11&jvmVariant=hotspot#x64_win-jdk), and follow the installation instructions.

### CentOS 7

**Note for lab machines in 2.11:**

OracleJDK should already be install at `/usr/java/jdk1.8.0_111`, but you have to set the
proper `JAVA_HOME` via `export JAVA_HOME="/usr/java/jdk1.8.0_111"`. You may want
to add this to your `.bashrc`.

**For any other CentOS machines:**

CentOS' yum repository seems to only contain old versions of JDK and
due to licensing issues, JavaFX jars are excluded intentionally.

To obtain the latest Oracle JDK which has the JavaFX jar bundled, follow
the instructions below:

 1. Download the Oracle JDK package:
    `wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.rpm"`
     or download it manually from the
     [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
     website
 2. Install the downloaded package by typing:
    `sudo yum localinstall jre-8u102-linux-x64.rpm`,
    JDK should be installed at `/usr/java/jdk1.8.0_102/jre/bin/java`

**NOTE**: If you have multiple versions of Java installed, you may
select the default version to use via `alternatives --config java`

### Linux

Ubuntu's package repositories contain an up-to-date OpenJDK with latest
JavaFX jar as a separate package.

 1. Update apt by typing `sudo apt-get update`
 2. Install OpenJDK and OpenJFX by typing `sudo apt-get install openjdk-8-jdk openjfx libopenjfx-java`

Other Linux distribution should have similar packages, which you can obtain
through the corresponding package manager.


### macOS / OS X

Download the latest JDK 8 from
[Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html),
choose the `Mac OS X` package and follow the installation instructions.
**Note**: You might be presented with Java 9 as being the latest version, in
which case you will need to manually choose the latest Java 8 package.

Alternatively, if you use [Homebrew](https://brew.sh/)<sup>†</sup>:

    brew tap caskroom/versions
    brew cask install java8

See [this Stack Overflow
question](https://stackoverflow.com/questions/24342886/how-to-install-java-8-on-mac)
for more information.

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

The easiest way to make sure you're using the correct Java version (Java 8) is
to not have any other versions installed. If you _need_ other versions, then you
should make sure that you use Java 8 for the coursework. If you use an IDE,
there should be a setting allowing you to choose which JDK you use, and on Linux
you can use
[update-alternatives](https://linux.die.net/man/8/update-alternatives) (or
[update-java-alternatives on Ubuntu](https://askubuntu.com/questions/315646/update-java-alternatives-vs-update-alternatives-config-java)).

To uninstall Java 9 (or other unsupported versions):

* On Windows, use the Control Panel.
* On Linux, use your package manager, e.g. `apt remove openjdk-9-jdk`.
* On Mac, depedning on how you installed Java:
  - Using Homebrew: `brew cask uninstall java`
  - Manually using a package downloaded from the Oracle website (note the
  version number in the first command, which you may need to change according to
  what you installed):

  ```
  sudo rm -rf /Library/Java/JavaVirtualMachines/jdk-9*.jdk/
  sudo rm -rf /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
  sudo rm -rf /Library/PreferencePanes/JavaControlPanel.prefPane
  ```

