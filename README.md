# hub
Welcome to the Robocorp hub content experiment
# Overview
Robocloud is set up in a hierarchical way. At the top, we find the Organizations, under which Workspaces are created, that contain Processes, which use Activities from Activity Packages. Activities inside processes are then run by Workers. Processes in the same workspace have access to the same Vault. Activities in the same process can share information using the Work Item.

# Let's look at these concepts one by one:

# Organizations
Organizations group and provide access control and administrative features to workspaces and users. Users belonging to the same organization can collaborate on creating and maintaining software robots in shared workspaces. Users can belong to more than one organization and can create organizations as needed. Billing happens at the organization level.

# Workspaces
When you register to Robocloud, you get your own workspace. When working with other developers, you will want to create a common workspace. Processes are created into workspaces, and Vault secrets and Workers are workspace-specific.

# Processes
To run a software robot in Robocloud, you execute a Process. Processes are created within workspaces, and users need to have access to a workspace to execute and edit the processes contained in it. When creating a process, you will choose which activities are executed, in which order, and by which worker. Processes can be scheduled and triggered either manually in the Robocloud UI or via an API.

# Activities
An Activity is a reusable part of a process that can be executed in isolation of other activities. You can configure a process to run multiple activities in sequence. A good reason to divide your robot along activity lines is that an activity can be run only by one worker. For example, if you have a multi-step process that needs to partly be run on the cloud and partly on self-hosted machines, you can divide it into two activities and configure each of them independently when creating a process.

The most common use case is to trigger a Robot Framework script, but you can configure an activity to run Python scripts directly or even programs written in any language.

# Activity packages
You can import your activities into Robocloud as zip files, that follow the activity structure guidelines. A package can include more than one activity. Activities in the same package can easily share code and needed data. One activity package is edited at a time in Robocode Lab. For example, you could create one activity package that groups all activities that work with one target system, for example, Excel or SAP.

# Worker
The processes and activities that Robocloud controls are ultimately run by Robocloud Workers. A worker can be a cloud worker (a Docker container), or a local worker, running on a Windows, macOS, or Linux machine. One Robocloud Worker executes one activity for one work item at a time in an isolated environment. The worker takes care of creating the correct environment for the activities to be run successfully, wherever it is executed.

# Work Item
Activities in the same Process can share data during their execution, thanks to the concept of Work Item. Each activity execution receives a work item from the previous activity and passes it forward to the next one. During the execution, each activity can freely read and update the data contained in the item. It is also possible to configure an activity to accept an initial work item and pass the desired contents when triggering the process that contains the activity via an API call.

# Vault
Vault provides a way to store credentials and other sensitive information inside Robocloud that your activity code can easily access and make use of. Vault secrets are tied to a specific workspace.
