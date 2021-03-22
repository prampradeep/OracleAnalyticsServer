
# Oracle Analytics Server Installtion

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



Before we goahead with the software install we need to make sure to have the right folder structure to host the Fusion middleware software. Below is the recommended approach, to have the Oracle_Home and Domain_Home in different directories which will help in future upgardes.


## Response Files

Response files contain information which is entered while using the GUI and is essential for Installtion. We need to make sure the respose files are ready before proceeding with installtion. Sample respose files are attached.

  -  fmw.response
  -  oas.response
  -  config.response 

