
# Groovy scripts to add and remove Continous Delivery configuration steps into Jenkins

You can run these groovy scripts via the Jenkins Groovy Console to add and remove CD config steps. 
Since there are several elements to modify, having a script will vastly improve the productivity.

Read 'How to run the Script' for some important information.

## To run the script

1.To run the script for a single project, add a value to projName and comment out the line with "item.name ==~/carbon-([a-zA-Z])+/)" and run the script.

```
 String projName="carbon-data"
   // if(!item.disabled&&item.getLastBuild()!=null&&(item.name ==~/carbon-([a-zA-Z])+/)){
   if(!item.disabled&&item.getLastBuild()!=null&&(item.name ==projName)){
```

2.To run the script for matching patterns that has a project name like carbon-data/carbon-uuf,
uncomment the line with (item.name ==~/carbon-([a-zA-Z])+/)

```
 //String projName="carbon-data"
    if(!item.disabled&&item.getLastBuild()!=null&&(item.name ==~/carbon-([a-zA-Z])+/)){
  // if(!item.disabled&&item.getLastBuild()!=null&&(item.name ==projName)){
```

3.Paste the script on `Script Console` page available under the `Manage` Jenkins page in the left menu.
Then, click on run button to execute.


## Source code management: Credentials Select
This script will help to Change the credentials for GIT Source code management. 
To change the credentials pass the value to the credentialsId variable within the script 
Ex: String credentialsId="4ff4a55b-1313-45da-8cbf-b2e100b1accd"


## Source code management :Wipe out workspace & force clone

This script will help to add an additional behavior for source code management by adding wipeout workspace & force clone option within the project configuration


## Build Environment: MaskPassword plugin

This script will help to tick off the mask password checkbox for the projects. 
Running this script on script console will ensure that the option[1] is checked.

[1]Mask passwords (and enable global passwords)


## Build Environment:Maven ReleaseBuild
This script will help to tick off the Maven release related option for the projects. 
Running this script on script console will ensure that the option[1] is checked. 

[1]Maven release build


Note:To change the parameters for Release goals and options[2] and DryRun goals and options[3] update the below two parameters

[2]DEFAULT_RELEASE_GOALS
[3]DEFAULT_DRYRUN_GOALS

## Post Build Actions
This script will help to fill the Post Build Actions related option for the project. 
Running this script on script console will ensure that the option[1] is filled. 

[1] Release environment variable

Note:To change the parameters for Release environment variable, update the below  parameter[2] 

[2]releaseEnvVar="IS_M2RELEASEBUILD";


=================
Add/Remove Trigger
=================
This script will help to change the build triggers for the projects. Running this script on script console will ensure that the option[1] is unchecked and option[2] is checked

[1]Poll SCM

[2]Build when a change is pushed to GitHub