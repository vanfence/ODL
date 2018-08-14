
#Develop APPs on OpenDaylight Controller-- Hello Rpc implementation

1.prequisites

  a.  Maven 3.1.1 or later

  b.  Java 7- or Java 8-compliant JDK

  c.  An appropriate Maven settings.xml file:

 Use opendaylight settings.xml to modify the maven ~/.m2/settings.xml
 

    $ cp -n ~/.m2/settings.xml{,.orig} ; /
 
      wget -q -O - https://raw.githubusercontent.com/opendaylight/odlparent/master/settings.xml > ~/.m2/settings.xml
 

 or specify the version of opendaylight like this:
 
 
    $ cp -n ~/.m2/settings.xml{,.orig} ; /
 
      wget -q -O - https://raw.githubusercontent.com/opendaylight/odlparent/stable/carbon/settings.xml > ~/.m2/settings.xml

2.Create a hello project using Maven and an archetype called the opendaylight-startup-archetype

    $ mvn archetype:generate /
 
      -DarchetypeGroupId=org.opendaylight.controller /
 
      -DarchetypeArtifactId=opendaylight-startup-archetype /
 
      -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/<opendaylight.release | opendaylight.snapshot>/
 
      -DarchetypeCatalog=remote /
 
      -DarchetypeVersion=Archetype-Version
 
  
  Attention:
  
   I. the correct Archetype-Version one can be found at https://nexus.opendaylight.org/#nexus-search;quick~opendaylight-startup-archetype
   
  II. if  Archetype-Version==*-SNAPSHOT 
  
       -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/opendaylight.snapshot/
  else:
  
       -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/opendaylight.release/

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
   
      $ sudo apt-get removw openjdk*
     
  b. download the jdk file
   
      $ wget http://www.oracle.com/technetwork/java/javase/downlaods/jdk-8u101-linux-x64.tar.gz 
      
      $ mv  jdk-8u101-linux-x64.tar.gz  /home/Applications
      
      $ tar -zxvf jdk-8u101-linux-x64.tar.gz
      
  c. config the environment path(write the following path into ~/.bashrc or /etc/profile)
   
      export JAVA_HOME = /home/Applications/jdk1.8.0_101
      
      export JRE_HOME = $JAVA_HOME/jre
      
      export CLASSPATH = .:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
      
      export PATH = $JAVA_HOME/bin:$JRE_HOME/bin:$PATH
      
      $ source ~./bashrc / source /etc/profile
    
  d. check the java 
    
      $ java -version
      
 
 2. Maven 3.3.9
 
   a. download the apache maven file 
   
   b. config the environment path(to ~./bashrc or /etc/profile)
   
      export M2_Home = /home/Applications/apache-maven-3.3.9
      
      export M2 = $M2_home/bin
      
      export PATH=$M2:$PATH
      
      MAVEN_OPTS = "-Xmx2048m -XX:MAxPermSize=512m"
      
      $ source ~./bashrc
      
   c. check the maven
   
      $ mvn -v
      
      
 3. Git
 
     first step : $ sudo apt-get install git
     
     second step: export GIT_SSL_NO_VERIFY = 1  > ~./bashrc file(No need to verify the git)
     
     third  step:  $ source ~/.bashrc
     
      
   

