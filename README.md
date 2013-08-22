===============================================================================
    jmx-staticport-agent
===============================================================================

Expose JMX MBeans over a specific network interface (Different than default 
getHostByName function result), and a target port.

All network communications will me made over :
 - The specified interface, without using any DNS lookup.
 - The specified port and only this one. (Not random range like default behaviour)

Building from sources :
===============================================================================

git clone git://github.com/mchaplin/jmx-staticport-agent.git

mvn package

Binary release is available under target/jmx-staticport-agent-1.0.0.jar

Usage :
===============================================================================

Add a -javaagent arg to your Java command line. ex :

    java -jar foo.jar -javaagent:/path/to/jmx-staticport-agent-1.0.0.jar

By default, the agent will bind to 127.0.0.1:6001
You can specifiy an alternate adress and port with the following system properties 

-Dstatic.jmx.agent.host=<IPV4>
-Dstatic.jmx.agent.port=6001

Ex :

    java -jar foo.jar -Dstatic.jmx.agent.host=10.5.14.132 -Dstatic.jmx.agent.port=3768 -javaagent:/path/to/jmx-staticport-agent-1.0.0.jar

You also need to add the JAR archive into the classpath of your JMX client. For example, with jVisualVM :

    /usr/lib/jvm/jdk/bin/jvisualvm -cp:a /path/to/jmx-staticport-agent.jar