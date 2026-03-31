Title: Install Java JDK 21 (Windows, macOS, Linux)

**Purpose**

Install Java Development Kit (JDK 21) for development and runtime execution across environments.

**Reference:**

Official Oracle Downloads: [Download Java JDK](https://www.oracle.com/java/technologies/downloads/#jdk21-mac)

⸻

**Prerequisites**

	•	Admin / sudo access
	•	Internet connection
	•	Compatible OS (Windows, macOS, Linux)

⸻

**Supported Environments**

	•	Windows (x64)
	•	macOS (Intel / Apple Silicon)
	•	Linux (Debian, Ubuntu, RHEL, etc.)

Steps

Step 1: Download JDK 21

	•	Go to Oracle download page
	•	Accept license agreement
	•	Download based on OS:

**OS**   **File Type**


    Windows  .msi
    macOS    .dmg
    Linux    .tar.gz / .deb / .rpm

## Windows Installation

Step 2: Install JDK

Double-click jdk-21_windows-x64_bin.msi

	•	Follow installer wizard
	•	Click Next → Install → Finish 

Step 3: (Optional) Silent Install

    msiexec.exe /i jdk-21_windows-x64_bin.msi

Step 4: Set Environment Variables

	•	Go to: System → Advanced → Environment Variables

Add: 

    JAVA_HOME = C:\Program Files\Java\jdk-21

Update PATH: 

    %JAVA_HOME%\bin

## macOS Installation

Step 2: 
**Install JDK - Double-click downloaded .dmg file**

Then: 

**Double-click JDK 21.pkg → Continue → Install**

Installer wizard completes installation 

Step 3: Configure PATH
Open Terminal and paste the following:

    echo 'export PATH="/Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home/bin:$PATH"' >> ~/.zshrc
    source ~/.zshrc

## Linux Installation Option A:
 Using tar.gz

    cd /opt
    sudo tar -xvzf jdk-21_linux-x64_bin.tar.gz

JDK will be extracted into a directory like:
    /opt/jdk-21
```  [oai_citation:2‡Oracle Docs](https://docs.oracle.com/en/java/javase/21/install/installation-jdk-linux-platforms.html?utm_source=chatgpt.com)  

---

## Option B: Debian/Ubuntu (.deb)

        ```bash
        sudo dpkg -i jdk-21_linux-x64_bin.deb

Step 3: Set Environment Variables
Open Terminal and run the following:

    export JAVA_HOME=/usr/lib/jvm/jdk-21
    export PATH=$JAVA_HOME/bin:$PATH

**Verification**
Run in terminal:

    java -version


Expected Output:
**java version "21"**


##  Common issues

**Issue: java command not found**

Fix:

    export PATH=$PATH:$JAVA_HOME/bin

**Issue: Multiple Java versions conflict**

Fix:

    update-alternatives --config java

## Rollback

**Windows**
Uninstall via Control Panel

**macOS**

    sudo rm -rf /Library/Java/JavaVirtualMachines/jdk-21.jdk

**Linux**

    sudo rm -rf /usr/lib/jvm/jdk-21