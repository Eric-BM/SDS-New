# Exercise 2 - Docker advanced
## Assigments
1. Create a Docker compose file which defines two services - toyota-data-feeder application and mosquitto broker.  
    1. For toyota-data-feeder use the image you pushed to registry in exercise1.  
    2. Use the official [eclipse-mosquitto](https://hub.docker.com/_/eclipse-mosquitto/) image.  
    3. USE ONLY CHARACTERS a-z AND minus sign ( - ) IN SERVICE NAMES
2. Configure mosquitto broker with [correct configuration](https://mosquitto.org/man/mosquitto-conf-5.html) - encrypted unauthenticated access.  
    1. Broker should allow for anonymous access.  
    2. Use ports 1883 and 8883.  
    3. Use ca.crt, server.crt and server.key for enabling encrypted access.  
3. Mount configuration files and certificates to mosquitto container
4. Connect toyota-data-feeder to use mosquitto broker.  
    1. Create a custom network with the name of your studentid (studentXXX-net) in the docker compose file.  
    2. For feeder url and port use the locally deployed mosquitto sub. Don't use mqtt-test.rahtiapp.fi:443.
5. Run docker compose to start up the services
6. Confirm you are receiving messages to your localhost with mosquitto_sub
7. Showcase that your containers work in a custom network.  
    1. docker network inspect
    
## Deliverables
1. Zip -file with following files (7z, rar, tar accepted as well).  
    1. docker-compose.yml.  
    2. mosquitto.conf and certificates.  
    3. Other files needed for the deployment to work
2. Text report for describing each step. Also show your cli input's and output's.

### My Text Report
#### INFO:
   My name: Xinyuan Ma  
   CSC Rahti account: student297

#### STEPS:
1. Create a compose file named [docker-compose.yml](src/docker-compose.yml)
    1. Defines two services
       ``` yaml
        services:
           feeder:
              ...
           mosquitto:
              ...
       ```
    2. Use the official image
       ``` yaml
           image: eclipse-mosquitto:latest
       ``` 
    3. Create [correct configuration](src/mosquitto.conf)
        1. Broker should allow for anonymous access. 
        ``` conf
        allow_anonymous true
        ```
        2. Use ports 1883 and 8883.  
        ``` conf
            listener 1883
            listener 8883
        ```
        3. Use ca.crt, server.crt and server.key for enabling encrypted access.
        ``` conf
            certfile /mosquitto/config/certs/server.crt
            cafile /mosquitto/config/certs/ca.crt
            keyfile /mosquitto/config/certs/server.key
        ```