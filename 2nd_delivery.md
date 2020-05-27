# 2nd Delivery

### FeedBack of 1st Delivery

* **PROS**:
  * Focus on a very clear feature instead of presenting 10000 of foggy features
  > ✅ We add the feature of music generation that is correlated to the existent features

* **CONS**:
  * ❌ How to measure Accuracy of BLE: False Positive/Negative, Noise, etc. is not clear
  > ✅ In the Evaluation document we define some metrics for the BLE
  * ❌ Most frequently asked questions was not introduced in the presentation and it is a central chart
  > ✅ In the design document has been added a storyboard for the curators of the museum
  * ❌ The flow: problem, target, solution is not evident
  > ✅ In the Design document has been added the flow PROBLEM, SOLUTION, BENEFITS
  * ❌ Architecture make sense even if it is very basic
  > ✅ In the Architecture has been added the use of smartphone sensors, external sensors, Google Cloud Platform and a Recurrent Neural Network without changing the main idea of the chat

### Design, Architecture, and Evaluation updates

* **DESIGN**:
  1. Added the flow PROBLEM, SOLUTION, BENEFITS
  2. Added a storyboard for the curators to emphasize the use of the dashboard, which was not very clear in the 1st delivery
  3. Added a storyboard for the new music generation functionality

  [Design document](./Design.md)

<br>

* **ARCHITECTURE**:
  1. Added Google Cloud Platform with services: `IoT Core`, `Pub/Sub`, `AI platform`, `TensorFlow`, to manage the data coming from the sensors
  2. Added `Temperature` and `Humidity` sensors using STM32 Nucleo board and MBED-OS, to send data about museum ambient during the visit. Necessary for music generation
  3. Added smartphone sensors: `Accelerometer`, `Gyroscope`, `Ambient Light Sensor`, `Microphone` to send data about user activity during the visit inside the museum. Necessary for music generation
  4. Added Neural Network to generate music with the data the sensors
  5. Added X-NUCLEO-IDW01M1 for beacon wifi connection, needed to connect beacon with GCP
  6. Change Handlebars with AdminLTE for the dashboard because it is more reliable

  [Architecture document](./Architecture.md)

<br>

* **EVALUATION**:
  1. Added *Competitors* to show the main differences with some competitors
  2. Added *Functionalities implementation state* to show the development state
  3. Added *Beacon STM32 Evaluation* metrics to evaluate the beacon
  4. Added *Sensor measurements* that our plan to develop the sensor's interaction
  5. Added *Key Performance Indicators* to evaluate the software application and if it is user friendly

  [Evaluation document](./Evaluation.md)

### Functionalities implementantion state

* **2nd Delivery**: we focus our development on the mobile application BackEnd, in particular we implement the Authentication and the Chat. We set up the Google Cloud Platform with all the services we need. We create the Database and it is already online. All these features allow us to retrieve and manage the values that arrived from the sensors. Furthermore we create JS scripts to simulate the periodic sending of values to test if the BackEnd and the GCP are able to manage these data.

* **3rd Delivery**: Mentor logic, real hardware sensors implementation, finite-state automaton to transform the chat in a chatbot, convert data into musical notes, Neural Network to generate music

Detailed information about the functionalities implementantion state are available in [Evaluation document](./Evaluation.md)

### Evaluation conducted



