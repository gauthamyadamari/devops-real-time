This file contains information regarding the following DevOps tools:
     1. Jenkins
     2. Docker
     3. kubernetes(k8S)
     4. MongoDB
     5. ReactJS
     6. Flask
#1.Jenkins: Jenkins is an open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration, and continuous delivery. It is a server-based system that runs in servlet containers such as Apache Tomcat. It supports version control tools, including AccuRev, CVS, Subversion, Git, Mercurial, Perforce, ClearCase, and RTC, and can execute Apache Ant, Apache Maven, and sbt based projects as well as arbitrary shell scripts and Windows batch commands.

##Builds: Builds can be triggered by various means, for example:

    (a)a webhook that gets triggered upon pushed commits in a version control system
    (b)scheduling via a cron-like mechanism
    (c)requesting a specific build URL.
    (d)after the other builds in the queue have completed
    (e)invoked by other builds

###Plugins: Plugins have been released for Jenkins that extend its use to projects written in languages other than Java. Plugins are available for integrating Jenkins with most version control systems and bug databases
 --some of the plugins are as follows:
 (A) Mailer:
            Allows configuring email notifications for build results. Jenkins will send emails 
            to the specified recipients whenever a certain important event occurs, such as:

            (1)Failed build.
            (2)Unstable build.
            (3)Successful build after a failed build, indicating that a crisis is over.
            (4)Unstable build after a successful one, indicating that there's a regression
 (B) Credentials:
             (1)Allows storing credentials in Jenkins
 (C) SSH agents:
             (1)Open a SSH connection to the specified host as the specified username,
             (2)Check the default version of Java for that user,
             (3)[not implemented yet] If the default version is not compatible with Jenkins's 
                agent.jar, try to find a proper version of Java
             (4)Once it has a suitable version of Java, copy the latest agent.jar via SFTP (falling 
                back to scp if SFTP is not available),
                Start the agent process..
 