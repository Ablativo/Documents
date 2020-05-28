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

  * ❌ The flow: problem, target, the solution is not evident

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

* **2nd Delivery**: we focus our development on the mobile application, in particular, we implement the Authentication and the Chat. We set up the Google Cloud Platform with all the services we need. We create the Database and it is already online. All these features allow us to retrieve and manage the values that arrive from the sensors. Furthermore, we create JS scripts to simulate the periodic sending of values for humidity, temperature, and heart rate sensors, to test if the BackEnd and the GCP are able to manage these data.

* **3rd Delivery**: Mentor logic, real hardware sensors implementation, smartphone sensors, finite-state automaton to transform the chat in a chatbot, convert data into musical notes, Neural Network to generate music

Detailed information about the functionalities implementantion state are available in [Evaluation document](./Evaluation.md)

### Evaluation 

* **2nd Delivery**: 
  * About the **user experience** we have identified some measures to be followed in the development of the application. These measures are based on the KPI logic: Key Performance Indicator. 
  * From a **technical** point of view, we can group the work into three parts: Environmental sensors, Beacon, and Mobile Application. With respect to the 1st delivery, we add some environmental sensors: Temperature, humidity, and heart rate sensor. These sensors must be associated with a Nucleo board and must send the values to GCP with the MQTT protocol. We decided, for this delivery, to simulate them with a JS script sending random values every 5-10 minutes. For the beacon, we have identified some measures: Accessibility, Complexity, Robustness, Scalability, Cost, Security, Failure detection. Also for the mobile application, we have the same measures but due to the fact that it must be able to detect the beacon, we added: Accuracy and Precision. 
  * Finally we add an analysis of our possible **competitors** noticing that our two main features, interaction with a Chatbot to simulate a conversation and Generation of a melody based on the emotions of the user, aren't present in other already done products.

Detailed information about the Evaluation are available in [Evaluation document](./Evaluation.md)

* **3rd Delivery**:
  * From a technical point of view we must be able to collect data from the smartphone sensors and collect them in the database. We must be able to extract values from real sensors. The Nucleo Board must be able to send temperature and humidity to the cloud with the MQTT protocol. We must be able to collect data from the Heart rate sensor. We have to implement a chatbot with a finite-state automaton and the mentor in such a way that the interaction must be as real as possible. We must be able to convert data from the sensor into musical notes with some Music Algorithm. Finally, we have to train a Neural Network to transform musical notes, with the objective that the resulting melody must be nice and audible for the user.