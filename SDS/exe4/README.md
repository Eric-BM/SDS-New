# Exercise 4 - Kubernetes Advanced
## Assigments
1. Create two new yaml files with following definitions:
First yaml file:
Object definition for node-RED
Service for node-RED
Route for node-RED

Second yaml file:
PersistentVolumeClaim


Object definition for node-RED should include the following:
Use deployment or deploymentConfig
Use image: nodered/node-red
Mount directory /data with volumeMount
Create a volume for the mounted directory
Declare a persistentVolumeClaim for the volume and give it a name

Service for node-RED should include the following
Use port: 1880
Type: LoadBalancer


Route for node-RED
Use spec.host: nodered.<yourStudentId>.rahtiapp.fi

PersistentVolumeClaim (Separate yaml file!)
Use spec. accessModes:
        - ReadWriteOnce


2. Use “oc create” command to create the objects defined in your yaml files in Rahti

Inspect your deployment with "oc get all" and “oc status”
Use "oc get pod" to get node-RED pod name, should be something like nodered-75883903-hwk9y
Use "oc exec <podname> -i -t -- sh" (e.g. "oc exec nodered-75883903-hwk9y -i -t -- sh") to get access inside the container.
Once inside use “cd /data” to get into /data folder. Check with "ls"
Use “echo hello > hello.txt” to create hello.txt file with text hello. Check that file was created with “cat hello.txt”
Exit pod with “exit” command. Destroy pod with “oc delete pod nodered-pod”. Use “oc replace –force -f “<yourYaml>.yaml””. Use “oc get pods” and wait until pod is ready. Repeat steps 3 and 4. Pod names should be different! Do not create a  new hello.txt file. Check that persistent volume works with "cat hello.txt"
3. Read https://nodered.org/docs/tutorials/

4. Edit flow.json file. Change the text inside the comparison operators <>. e.g. "topic": "<studentID>/#", change into "topic": "student123/#",

5. With your browser go to nodered.<yourStudentId>.rahtiapp.fi. Add node-red-dashboard, by clicking the menu (upper right corner) and selecting "manage palette". Select install tab and type "node-red-dashboard". Install it. Import flow.json by copypasting it into import prompt. Select menu> import. Upload certificates. Click Deploy.

6. Use image from exercise 1 to run an MQTT publisher on your own machine. Use MQTT_URL=mqtt.<studentXXX>.rahtiapp.fi and MQTT_PORT=443 in the docker run command.

7. Go to nodered.<yourStudentId>.rahtiapp.fi/ui. Check that speedometer is moving. Take a screenshot.

USE ONLY CHARACTERS a-z AND minus sign ( - ) IN SERVICE NAMES


## Deliverables

1. Two yaml files. First defining at least a Deployment, a Service, an Route and second yaml with PersistentVolumeClaim Object definition-

2. Short text report with screenshots from the inputs and output of all of the commands in tasks 2 including commands in subtasks.

3. Screenshots of working node-red speedometer and modified flow.json file

Possibly useful commands:

oc –help

oc create -f <your>.yaml

oc status

oc replace –force -f <your>.yaml

oc delete –all service (OR route OR configmap OR deployment OR etc..)

oc get pods (OR routes OR deployments OR etc..)





### My Text Report
#### INFO:
   My name: Xinyuan Ma  
   CSC Rahti account: student297

#### STEPS: