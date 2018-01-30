# Development environment setup

In order to start working on the  cw-model and cw-ai coursework, 
your machine needs to have Java 8u102 or newer installed. 


## CentOS 7

**Note for lab machines in 2.11:**

OracleJDK should already be install at `/usr/java/jdk1.8.0_111`, students MUST set the proper JAVA_HOME via
`export JAVA_HOME="/usr/java/jdk1.8.0_111"`, they may want to add this to their `.bashrc`.

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

## Ubuntu

Ubuntu's apt repository contains an up-to-date OpenJDK with latest 
JavaFX jar as a separate package.

 1. Update apt by typing `sudo apt-get update`
 2. Install OpenJDK and OpenJFX by typing `sudo apt-get install openjdk-8-jdk libopenjfx-java`


## macOS / OS X

Download the latest JDK from 
[Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
, choose the `Mac OS X` package and follow the installation instructions. 


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

Confirm the installation by typing `java -version` and 
    `echo $JAVA_HOME`

## Windows

Download the latest JDK from 
[Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html),
choose the appropriate Windows package and follow the installation 
instructions.

Add Java to `PATH` and setup `JAVA_HOME` so that other tools such as 
the console can find where Java is.

 1. Open *Control Panel*, in `\System and Security\System` click 
    on `Advanced system settings` on the left
 2. Open `Environment Variables...` on the bottom
 3. Find `Path` or `PATH` in the User variable list, create one if it
    does not already exist. Set the value to the `bin` directory of 
    your Java install, eg: `C:\Program Files\Java\jdk1.8.0_102\bin`
 4. Add a new variable and name it `JAVA_HOME` in User variable list,
    set the value to the install directory, eg: 
    `C:\Program Files\Java\jdk1.8.0_102`
 5. Restart to see changes
 
  
**NOTE**: x64 systems must install the `Windows x64` package otherwise 
JavaFX and other development tools might not work properly.
