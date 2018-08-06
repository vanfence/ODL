
#Develop APPs on OpenDaylight Controller-- Hello Rpc implementation

1.prequisites

 (1)Maven 3.1.1 or later

 (2)Java 7- or Java 8-compliant JDK

 (3)An appropriate Maven settings.xml file:

 Use opendaylight settings.xml to modify the maven ~/.m2/settings.xml:
 
 cp -n ~/.m2/settings.xml{,.orig} ; 
 wget -q -O - https://raw.githubusercontent.com/opendaylight/odlparent/master/settings.xml > ~/.m2/settings.xml

 or specify the version of opendaylight like this:
 
 cp -n ~/.m2/settings.xml{,.orig} ; 
 wget -q -O - https://raw.githubusercontent.com/opendaylight/odlparent/stable/carbon/settings.xml > ~/.m2/settings.xml

2.Create a hello project using Maven and an archetype called the opendaylight-startup-archetype

 mvn archetype:generate 
 -DarchetypeGroupId=org.opendaylight.controller 
 -DarchetypeArtifactId=opendaylight-startup-archetype 
 -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/<opendaylight.release | opendaylight.snapshot>
 -DarchetypeCatalog=remote 
 -DarchetypeVersion=Archetype-Version
 
  
  Attention:
  
   I. the correct Archetype-Version one can be found at https://nexus.opendaylight.org 
   
  II. if  Archetype-Version==*-SNAPSHOT 
  
       -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/opendaylight.snapshot/
  else:
  
       -DarchetypeRepository=https://nexus.opendaylight.org/content/repositories/opendaylight.release/

 for example:
 
 mvn archetype:generate 
 -DarchetypeGroupId=org.opendaylight.controller 
 -DarchetypeArtifactId=opendaylight-startup-archetype 
 -DarchetypeRepository= http://nexus.opendaylight.org/content/repositories/opendaylight.release/ 
 -DarchetypeCatalog=remote  
 -DarchetypeVersion=1.3.0-Carbon (be the same version--carbon as the upper one in the settings.xml)
 
     
3.Build the module and implement the HelloWorld RPC API:
   
   search https://docs.opendaylight.org/en/stable-oxygen/developer-guide/developing-apps-on-the-opendaylight-controller.html 
   for appropriate operations
