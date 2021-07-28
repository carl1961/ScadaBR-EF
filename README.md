# ScadaBR-EF

### You can download the most current version of ScadaBR-EF [here](https://github.com/celsou/ScadaBR-EF/releases/latest). I will hardly release new versions in the near future (reason: I went to college).

## About
The Enhanced Font-end (ScadaBR)[EF) is an experimental project, with no direct link to the original ScadaBR or scada-LTS. The main intention of this project is to generate a stable and more up-to-date version of ScadaBR with the technologies available in 2021, through a front end with several visual and usability improvements. In addition, ScadaBR-EF brings several fixes of small bugs that improve the user experience on a daily life.

## Installation
From release 2, ScadaBR-EF has installers for Windows and Linux, get them on the [releases page](https://github.com/celsou/ScadaBR-EF/releases/latest/).

If you want or need to perform a manual installation, follow these steps:
- Install Java (or [OpenJDK](https://adoptopenjdk.net/releases.html?variant=openjdk8&jvmVariant=hotspot)) 8
- Install [Tomcat 8.5](https://tomcat.apache.org/download-80.cgi) or [Tomcat 9](https://tomcat.apache.org/download-90.cgi)
- Download [last release](https://github.com/celsou/ScadaBR-EF/releases/latest/)
- Extract the '.war' file and copy the extracted folder into the 'webapps/' folder in Tomcat
- Restart Tomcat

Note: The database used by default is Derby. If you want to use another database (such as MySql) the configuration to be performed is the same as for other versions of ScadaBR (that is, editing the file '/WEB-INF/classes/env.properties').


## Is ScadaBR-EF stable?
In theory, yes. Since the focus of this project is to improve the front end of ScadaBR, few changes to the Java code itself have been. Therefore, the ScadaBR-EF should be as stable as ScadaBR 1.1 CE, on which it was based. However, since I could not perform many tests in real scenarios (of communication protocols), it is not possible to guarantee that ScadaBR-EF actually works satisfactorily for all cases.

## ScadaBR-EF vs. ScadaBR 1.1CE vs. Scada-LTS
ScadaBR-EF was not created with any intention of being a Competitor of Scada-LTS or a division in the original ScadaBR project. The Scada-LTS is much superior to the ScadaBR-EF, however, as its development has not yet reached a stable "final" version, and as ScadaBR is currently attached to Java 6, the ScadaBR-EF was thought to possibly be adopted as an "intermediary" to fill the gap between the current ScadaBR (1.0/1.1) and the future Scada-LTS.



Resources  | ScadaBR 1.0 | ScadaBR 1.1 | ScadaBR-EF | Scada-LTS
---------- | ----------- | ----------- | ---------- | ---------
Java version | 6th | 7 or 8 (depends on build) | 8th | 11
User profile page | You don't have | It | It | Has
REST api | You don't have | You don't have | You don't have | Has
Active development | Don't | Don't | No (just occasional releases) | yes
Modbus Serial | Yes | Don't | Yes (Release 3+) | No (but will be implemented in the future)
Installers | Windows, Linux (unofficial), manual installation | No official installers, only manual installation or unofficial installers | Windows, Linux (including Raspberry), manual installation | Docker installation or manual installation


## Where does the ScadaBR-EF run?
I'm successfully running ScadaBR-EF on Linux Mint 19.1 (based on Ubuntu 18.04) with OpenJDK 8 (equivalent to Java 8) and Tomcat 8/9.
My **.war** files were compiled in Eclipse, version 2020-12 (4.18.0).
The source code I pulled from SourceForge and brought it to GitHub. Since I don't know much about Java and Eclipse, I can't say this repository can be cloned and compile on another computer without having to change some configuration.

## Known bugs
- I experienced problems with OpenJDK 8 when sending emails. If you receive an error alarm containing the message 'javax.net.ssL.SSLExceptionHandshake: No appropriate protocol (protocol is disabled or cipher suites are inappropriate)' edit the file 'java.security' (which must be in '$JRE/lib/security/java.security', in my case was in '/etc/java-8-openjdk/security/java.security') and in the option 'jdk.tls.disabledAlgorithms' remove 'TLSv1' and 'TLSv1.1' from the list.
- You can only open one Graphical Representation at a time in the same browser. This limitation, inherited from ScadaBR, is quite complex and I could not solve it in ScadaBR-EF, unfortunately.
