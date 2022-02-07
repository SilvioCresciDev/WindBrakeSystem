# Wind Brake System
University project for Serverless course

Did you know that the weight of the wind turbines alone reaches 500t? Think what would happen if these broke off due to the strong wind and fell on houses or roads. Fortunately, the wind turbines are equipped with braking systems ready to activate and avoid such disasters. 

In this IoT project, a sensor will detect wind speed values and brake wear percentage and send them to a queue of the RabbitMQ message broker. Then the consumer reads the messages, and determines whether the wind speed is high enough to activate the brakes and whether maintenance is required due to wear. Then send a message to 2 different queues: one where is a listening a BrakeSystem which will activate or deactivate the brake of wind turbines, and another to a NotificationSystem which will notify the user if maintenance is required.

<p align="center"><img src="/Assets/ArchitectureWindBrakeSystem.png" width="900"/></p>

# Requirements

- Ubuntu 20.04
- Docker and Docker Compose 
- Nuclio
- RabbitMQ
- nodeJS



## Installation
Install nodeJS and all the needed library:

```bash
sudo apt install nodejs

npm install amqplib

npm install mqtt

```

## Usage


Start [Nuclio](https://github.com/nuclio/nuclio) using a docker container.

```sh
docker run -p 8070:8070 -v /var/run/docker.sock:/var/run/docker.sock -v /tmp:/tmp nuclio/dashboard:stable-amd64
```
Start [RabbitMQ](https://www.rabbitmq.com) instance with MQTT enabled using docker.

```sh
docker run -p 9000:15672  -p 1883:1883 -p 5672:5672  cyrilix/rabbitmq-mqtt 
```
Now you can import the functions into Nuclio dashboard and run them from there or with the provided script.

Don't forget to start the three scripts for show the outputs
```sh
node logger.js
node logger2.js
node logger3.js
```

 


