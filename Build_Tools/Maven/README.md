# Maven - Java Build Tool  

•	Maven is a powerful build automation and project management tool, primarily used for Java-based projects. 

•	It simplifies the process of building, managing dependencies, and documenting software projects. 

•	Maven projects are defined by a Project Object Model (POM) pom.xml file & has a lifecycle.

•	pom.XML file contains project configurations, dependencies, plugins, and other information required for building the project.

```
Source code (.java files)
Maven (pom.xml) 
Executable File (binary -.exe, .jar,.apk files)

Flow: .Java → maven → pom.xml → artifact id, version, package, dependency, lifecycle, distribution management.

```


##  Maven pom.xml structure
```
my-project name 
├── src
│   ├── main
│   │   ├── java        # Java source code
│   │   ├── resources   # Resources like configuration files
│   │   └── webapp      # Web application resources (for web projects)
│   │
│   ├── test
│          ├── java        # Test source code
│          └── resources   # Test resources
│
├── target             # Compiled bytecode and packaged JARs
├── pom.xml            # Project Object Model configuration file
├── .gitignore         # Git ignore file (if using Git)
└── README.md          # Project documentation
```

# Lifecycle:
 
  ### Phases of Maven Lifecycle

mvn clean 	-> cleans your previous work environment

mvn validate	-> validates the project necessary application file+pom.xml file's availability

mvn compile	-> compile the code (java → bytecode) human readable file to machine readable format

mvn test	-> runs the local tests setup by developer

mvn package	-> bundles the src code in a single executable jar file

mvn install	-> places the executable file into local repository(~./m2)

mvn deploy	-> pushes artifacts into remote repo.(jfrog, docker registry, maven central repo - online repo)

#### NOTE:

•	local repo → ~./m2 directory

•	central repo → looks for online repo maven.central

•	settings.xml - handles username & password credentials that lets to connect with remote repo to push artifacts.

•	If we run mvn deploy it automatically performs the previous phases from clean to install default.


### interview Q's - 

1.	mandatory fields that we need in pom.xml are
      1.	group id
      2.	artifact id
      3.	version
      4.	packaging
      5.	dependency block - plugins
      6.	if we want to push jar file then distribution management block

2.	the executable output file that maven generates will be of the below format

  	 1.	<artifact_id>-<version>.<packaging>
     
     ```
      EX:          helloworld-1.1.jar
      ==
      [ec2-user@ip-172-31-15-245 target]$ ll
      total 4
      drwxr-xr-x. 3 ec2-user ec2-user   17 Jul  1 11:36 classes
      drwxr-xr-x. 3 ec2-user ec2-user   25 Jul  1 11:36 generated-sources
      -rw-r--r--. 1 ec2-user ec2-user 3071 Jul  1 18:31 helloworld-1.1.jar >>>>>>>>>
      ```
