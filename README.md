
#Develop APPs on OpenDaylight Controller-- Hello Rpc implementation

1.prequisites

  a.  Maven 3.1.1 or later

  b.  Java 7- or Java 8-compliant JDK

  c.  An appropriate Maven settings.xml file:
  
   Use opendaylight settings.xml to modify the maven ~/.m2/settings.xml.
   OpenDaylight maintains its own repositories outside of Maven Central, which means maven cannot resolve OpenDaylight           artifacts  by default. Since OpenDaylight is organized as multiple inter-dependent projects, building a particular project       usually means pulling in some artifacts. In order to make this work, your maven installation needs to know the location of       OpenDaylight repositories and has to taught to use them.
    This is achieved by making sure ~/.m2/settings.xml looks something like the copy kept in odlparent
 
    $ cp -n ~/.m2/settings.xml{,.orig} ; /
 
      wget -q -O - https://raw.githubusercontent.com/opendaylight/odlparent/master/settings.xml > ~/.m2/settings.xml
      
      or
      
      (suggest) copy https://github.com/opendaylight/odlparent/blob/master/settings.xml setting.xml > ~/.m2/settings.xml
      
 

 or specify the version of opendaylight like this:
 
 
    $ cp -n ~/.m2/settings.xml{,.orig} ; /
 
      wget -q -O - https://raw.githubusercontent.com/opendaylight/odlparent/stable/carbon/settings.xml > ~/.m2/settings.xml
      
 Attention:
    If you get this Failure:
    
       [WARNING] Error initializing: org.codehaus.plexus.velocity.DefaultVelocityComponent
       java.lang.NoClassDefFoundError: org/apache/commons/lang/StringUtils
       
   Add this dependency in the:
  
        ~/.m2/repository/org/apache/maven/plugins/maven-archetype-plugin/{version}/maven-archetype-plugin-{version}.pom

2.Create a hello project using Maven and an archetype called the opendaylight-startup-archetype

    $ mvn archetype:generate /
 
      -DarchetypeGroupId=org.opendaylight.controller /
 
      -DarchetypeArtifactId=opendaylight-startup-archetype /
 
      -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/<Snapshot-type>/
 
      -DarchetypeCatalog=remote /
 
      -DarchetypeVersion=Archetype-Version
 
  
  Attention:
  
   I. the correct Archetype-Version one can be found at https://nexus.opendaylight.org/#nexus-search;quick~opendaylight-startup-archetype
   
  II. if  Archetype-Version==*-SNAPSHOT 
  
       -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/opendaylight.snapshot/
  else(suggest):
  
       -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/opendaylight.release/

 for example:
 
     For the Carbon snapshot use Snapshot-type=opendaylight.release Archetype-Version=1.3.0-carbon
     For Boron "SR1" use Snapshot-type=opendaylight.release Archetype-Version=1.2.0-Boron-SR1
     For the Boron snapshot use Snapshot-type= opendaylight.snapshot Archetype-Version=1.2.2-SNAPSHOT
 
 
 for example:
 
     $ mvn archetype:generate /
 
      -DarchetypeGroupId=org.opendaylight.controller /
 
      -DarchetypeArtifactId=opendaylight-startup-archetype /
 
      -DarchetypeRepository= http://nexus.opendaylight.org/content/repositories/opendaylight.release/ /
 
      -DarchetypeCatalog=remote  /
 
      -DarchetypeVersion=1.3.0-Carbon (be the same version--carbon as the upper one in the settings.xml)
 

3.Build the module and implement the HelloWorld RPC API:
   
   search 
   
   https://docs.opendaylight.org/en/stable-oxygen/developer-guide/developing-apps-on-the-opendaylight-controller.html
   
   for appropriate operations


 ------------------------------------------------------------------------------------------------------------------------
Complier enviroment

1. Oracle Java 8 JDK

   a. pre-clean the java environment
   
       $ sudo apt-get remove openjdk*
     
   b. download the jdk file
   
       $ wget http://www.oracle.com/technetwork/java/javase/downlaods/jdk-8u101-linux-x64.tar.gz 
      
       $ mv  jdk-8u101-linux-x64.tar.gz  /usr/lib/jvm
      
       $ tar -zxvf jdk-8u101-linux-x64.tar.gz
      
   c. config java environment (write the following configuration into ~/.bashrc or /etc/profile,take /etc/profile for example)
   
       export JAVA_HOME = /usr/lib/jvm/jdk1.8.0_101
      
       export JRE_HOME = $JAVA_HOME/jre
      
       export CLASSPATH = .:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
      
       export PATH = $JAVA_HOME/bin:$JRE_HOME/bin:$PATH
      
       $ source /etc/profile
       
       Note:the configuration can be writen into /etc/environment,but we do not suggest this configuration
    
    d. check the java 
    
       $ java -version
      
 
 2. Maven 3.3.9
 
    a. download the apache maven file 
   
    b. config the environment path(to ~./bashrc or /etc/profile)
   
        export M2_Home = /usr/lib/jvm/apache-maven-3.3.9
      
        export M2 = $M2_home/bin
      
        export PATH=$M2:$PATH
      
        MAVEN_OPTS = "-Xmx2048m -XX:MAxPermSize=512m" (optional)
      
        $ source ~./bashrc
      
    c. check the maven
   
        $ mvn -version
      
      
 3. Git
 
     first step : 
           
           $ sudo apt-get install git-core
     
     second step: 
            
            export GIT_SSL_NO_VERIFY = 1  > ~./bashrc file(No need to verify the git)
     
     third  step:  
     
            $ source ~/.bashrc
            
  4. Reference
    
    1.  https://wiki.opendaylight.org/view/GettingStarted:Development_Environment_Setup
    2.  https://blog.csdn.net/zswang9/article/details/80643616
    
     
      
   

