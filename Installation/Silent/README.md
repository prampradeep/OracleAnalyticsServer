
# Oracle Analytics Server - Silent Installation

Below is an outline of what steps to be performed for Installing Oracle Analytics Server in Silent mode (without GUI) very easily. It will be of great use in situaltions where you have to install on multiple nodes on regular basis, where you dont have GUI or you need to automate the install process.


## Pre-requisites

  - Make sure you have a Compatible Database running to host the metadata schemas and SYS user access to create those schemas. Refer to [certification matrix](https://www.oracle.com/middleware/technologies/fusion-certification.html)
  -  Download the Oracle Analytics Server software from [edelivery](https://edelivery.oracle.com)
  -  JDK installed as per the requirement from above certification matrix
  -  Operating System user should have access to read and execute the software files along with installtion rights on target directories


## Prepare Environment

Below are some of the simple checks we need to perform to make sure the environment is ready for installtion.

### Verify JDK 

Make sure your default java is pointed to the required JDK version. You can do this by using `java -version`

![JavaVersion](/Installation/Silent/images/JavaVersion.png)


### Install Directories

Before we goahead with the software install we need to make sure to have the right folder structure to host the Fusion middleware software. Below is the recommended approach, to have the Oracle_Home and Domain_Home in different directories which will help in future upgardes.

![InstallDirectories](/Installation/Silent/images/InstallDirectories.png)


## Response Files

Response files contain information which is entered while using the GUI and is essential for Installtion. We need to make sure the respose files are ready before proceeding with installtion. Sample respose files are attached.

  -  [fmw.response](/Installation/Silent/responseFiles/fmw.response)
  -  [oas.response](/Installation/Silent/responseFiles/oas.response)
  -  [config.response](/Installation/Silent/responseFiles/config.response)

## Fusion Middleware Infrastructure Installation

Unzip the fusion middleware infrastructure (~1.5GB) download file. Make sure to update the fmw.respose files as needed before running this command. 

    java -jar /u01/app/oas/softwares/fmw_12.2.1.4.0_infrastructure.jar -silent -responseFile /u01/app/oas/resposefiles/fmw.response

## Patch on WLS

Move the patch zip file to `[ORACLE_HOME]/OPatch` and unzip it there. change into the newly created path folder for ex `cd 30657796`.
To apply patch use the below command.

    [ORACLE_HOME]\OPatch\opatch apply -silent

## Oracle Analytics Server Installtion

Unzip the Oracle Analytics Server installer zip file (~3.5GB). Modify the oas.response file to the oracle_home path as per previous step.

    java -jar /u01/app/oas/softwares/Oracle_Analytics_Server_Linux_5.9.0.jar -silent -responseFile /u01/app/oas/resposefiles/oas.response

## Oracle Analytics Domain Configuration 

Update the config.respose to include details of the domain_home, Database details (hostname,port, servicename and SYS details) and port information etc.

    [ORACLE_HOME]/bi/bin/config.sh -silent -responseFile /u01/app/oas/resposefiles/config.response

In case you want to ignore pre-requisite checks for some reason use below command.

    [ORACLE_HOME]/bi/bin/config.sh -silent -responseFile /u01/app/oas/resposefiles/config.response -ignoreSysPrereqs
