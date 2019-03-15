#Multiplayer Android app game -- Smart Toys for Virtual Interaction
This app presents a smart toy application which allows users to control drone(s) from anywhere in the world simply with a working internet connection. The app uses HTTPS protocol (as well as supports MQTT) to allow secure communications with the IoT Hub. The app provides an interface to allow parents to play with their kids even when they are far away and enhances meaningful communication. The Smart Toy app uses the in-built mobile accelerometer to control the drone movement. The data is tranmitted to IoT Hub which in turn transmits the data directly to drone. We perform IoT edge computation on thee drone to compute the velocity and acceleration of the drone based on previous state. The data from the drone is transmitted back to the IoT Hub which is fed into Azure Stream Analytics. Azure Stream Analytics intelligently filters the data to only capture the data coming from the drone devices to IoT Hub, and writes it to Blob Storage. New writes to blob storage trigger an Azure function (https://github.com/mitshubh/azure-iot-function) which reads thee location of the drones at the given instant and computes the winning or losing score. The score is then pushed to the user Android devices using cloud-to-device messaging.

##How to Play?
1. Specify the IoT Device connection string to connect to the IoT Hub
2. Move your mobile phone to move the drone.

##Scoring?
1. If user A flies his or her drone oveer user B's drone --> User A gets a point
2. (Future) On collision, the colliding drones loose a point. This is based on the idelology that there could be more than 2 drones playing. 
