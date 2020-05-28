# Evaluation
This document aims to provide details on how to evaluate the product, first from a user experience point of view, and then from a technical point of view.

<div align="center"><img src="./img/kpi.png" width="600" /></div>

We based our evaluation model in the well known **Key Performance Indicators**. The generic identikit of the KPIs must meet certain characteristics: the indicators must be ***quantifiable*** (and therefore measurable); ***management***, i.e. they must indicate whether the company is growing or not; ***operational***, and therefore exercise an effective change in the strategy adopted; finally ***practical***, and therefore adaptable to business needs.

---
### Table of contents
* [User experience](#usex)

* [Technical aspects](#tech)

* [Functionalities implementantion state](#state)

* [Competitors](#comp)

---
## <a id="usex"></a>User experience

#### Users survey
To first evaluate the idea, we have used a survey, sharing it with our family, friends, and friends of friends. Indeed, by these feedbacks and suggestions, we (hopefully) understood where to make some changes, and especially if the final user would really like and possibly use the final service.

Here the anonymous results:
- [International](https://docs.google.com/spreadsheets/d/15IgMSvd-63VwI2cXw7SHC1U36O2IEgHQvG_yR56Y7Nk/edit#gid=675511585)
- [Italian](https://docs.google.com/spreadsheets/d/1EfuZT_q8hNwSY7gu_bXCDNayzk7qYUeNwSBV3rvE9xY/edit#gid=510814664)

Here the most relevant graphs:
- [International](./pdf/graph_international.pdf)
- [Italian](./pdf/graph_Italy.pdf)


We received more than 100 replies from Italian people, and more than 40 from people spread over 15 different countries.
| | Result |
|----|----|
1 | Over 90% of them believe this service would be useful to improve the learning of the fundamental characteristics of a work of art, help the museum to provide a better service, boost their curiosity, and would have fun trying the application.
2 | The same percentage of people would go to the museum to try the novelty, however, in Italy, only around 50% if they have already been there, while in the other countries this percentage increases to ~65%.
3 | Finally, over 80% of these people told us they are thinking to download for real our application on their smartphone.

#### Evaluation metrics
Now, let's define the parameters we will use for the final evaluation:
* **Accessibility**: any type of user who knows how to use a chat will be able to use Ablativo.
* **Simplicity**: Ablativo must be intuitive. 
    * The museum visitor can easily sign-in/sign-up and choose his/her mentor
    * The museum visitor can easily interact with the mentor, which will have as natural as possible human-like behavior
    * The museum visitor can easily interact with the statutes, which will have as natural as possible human-like behavior
    * The museum curator can easily understand and see the statistics of the metrics collected by the service
* **Usability**: The response times of the chat must be rapid otherwise this could lead the user to not use it
* **Graphic interface**: The interaction between the mentor and the works of art will seem as natural as possible. The overall interface must be user friendly.
* **Privacy & Security**: Ablativo doesn't store any type of sensible data, the passwords will be encrypted.

---
## <a id="tech"></a>Technical aspects
Technical evaluation is a fundamental step in our work.

### Environmental sensors measurements
* **Ambient sensors**: Let's assume we have N rooms inside the museum. We will put one STM32 Nucleo board per room. The nucleo board is made of `Temperature`, `Humidity`, and `Beacon`.
    * *2nd Delivery*: Temperature and Humidity sensors will be simulated with a JS script that generates random values and sends them to the cloud and to the backend of the application. We send the values every 5-10 minutes.
    Beacon will be simulated with a smartphone through the app [Beacon Simulator](https://play.google.com/store/apps/details?id=net.alea.beaconsimulator&hl=en)

    * *3rd Delivery*: The 3 sensors will be real.

* **Smartphone sensors**: we retrieve the values from the smartphone sensors of every user. These values will be real.
    * *3rd Delivery*: we will be able to collect the values with a frequency of 1Hz (1 message per second). The values will be grouped and sent periodically

* **Heart Rate sensor**:
    * *2nd Delivery*: The values will be simulated with a JS script that with a frequency of 1Hz generates random values and send them to the cloud and to the backend of the application.
    * *3rd Delivery*: This sensor will be possibly real. To do this we have 2 options: Smartphone Heart Rate sensor or Bend Heart Rate sensor.

**NOTE**: The simulated version of the sensors allow us to check the connection between the BackEnd of the application and the Google Cloud Backend
### Beacon STM32 
We based our analysis on some specific metrics: `Accessibility`, `Accuracy`, `Complexity`, `Robustness`, `Cost`, `Scalability`, `Security`. Together with these, depending on the component taken into consideration, there will be some more specific characteristics.

* ⚠️ Work in progress
* ✅ Completed
##### Metrics description
* **Accessibility**: indicates the ability of the technology to be exploited by the user.
* **Robustness**: the system's ability to resist interference and noise from nearby sensors
* **Scalability**: the scalability of a system ensures its normal operation even when the sphere of the application becomes larger.
* **Cost**: the cost of a system like this can depend on several factors. The most important ones include money, time, space, weight, and energy. The time factor is linked to installation and maintenance times.
* **Security**: security means the danger that data sent through the system will be violated or accessed by third parties.
* **Failure detection**: the system must be able to notify the museum if there is a fault.

##### Metrics evaluation
| Metrics | Status |Solution/Result |
| ------------- |:---:| :-----|
| `Accessibility` | ✅ | Battery-powered that can last up to 2 years, they can be placed on any surface, accessible from the mobile app |
| `Robustness` | ✅ | Strategic points where to place the sensor. 1 beacon per room instead of 1 beacon per statue
| `Scalability` | ✅ | Beacons transmit only output signals 
| `Cost` | ⚠️ | Cost of sensors (see [Architecture](./Architecture.md) section for more details) + Cost of Google Cloud Platform |
| `Security` | ✅ | Beacons transmit output signals, there is no intrinsic safety risk in the transmission |
| `Failure detection` | ⚠️ | Every 10 minutes the beacons sends an alive-messages to the cloud |

**NOTE**: we will be able to do some measures only when we have the sensors in the hand.

### Mobile app
##### Metrics description
* **Accessibility**: indicates the ability of the technology to be exploited by the user.
* **Accuracy**: average error in calculating the distance from the statues.
* **Precision**: how the system works overtime, how similar the various measurements are to each other, which does not necessarily mean that the system is accurate.
* **Complexity**: complexity can be attributed to hardware, software needed for the system.
* **Scalability**: the scalability of a system ensures its normal operation even when the sphere of the application becomes larger.
* **Cost**: the cost of a system like this can depend on several factors. The most important ones include money, time, space, weight, and energy.
* **Security**: security means the danger that data sent through the system will be violated or accessed by third parties.

##### Metrics evaluation
| Metrics | Status |Solution/Result |
| ------------- |:---:| :----- |
| `Accessibility` | ✅ | Accessible with a simple smartphone |
| `Accuracy` | ⚠️ | Calculated as the average of the Euclidean distance between the estimated and the real position |
| `Precision` | ⚠️ | Comparison of the various measurements |
| `Complexity` | ✅ | Thanks to the framework React native the implementation is very simple and fast |
| `Scalability` | ✅ | Being designed for an internal museum, it will have a number of connected users that will never be too high to affect scalability |
| `Cost` | ✅ | In the future to handle big amount of data MongoDB could be a cost (not for the initial setup) |
| `Security` | ✅ | All data provided by the users will be encrypted. No sensible data are needed |

**NOTE**: we will be able to do some measures only when we have the sensors in the hand.

---
## <a id="state"></a>Functionalities implementation state
Ablativo is made of five different components that need to fully interact with each other. These interactions must be well defined.
* ⚠️ Work in progress
* ✅ Completed
#### Mobile application - Beacon sensor
| Feature | Status |
| :---- | :----: |
| The mobile device must be able to broadcast and accept BLE packets | ✅ (PoC) |
| The mobile device must be able to read the UUID of the beacon it interacts with | ✅ (PoC) |
| If the user moves away, the mobile device must be able to understand that it is no longer near the work of art | ⚠️ |

#### Mobile application - Smartphone sensor
| Feature | Status |
| :---- | :----: |
| The mobile app must be able to retrieve values from the Accelerometer | ⚠️ |
| The mobile app must be able to retrieve values from the Gyroscope | ⚠️ |
| The mobile app must be able to retrieve values from the Microphone | ⚠️ |
| The mobile app must be able to retrieve values from the Ambient Light Sensor | ⚠️ |

#### Mobile-Application - BackEnd
| Feature | Status |
| :---- | :----: |
| The mobile application must be able to send the request to and receive a response from the back-end via HTTP through fetch construct | ✅ |
| The mobile application must be able to interact with the backend to establish a dialog between the user and the mentor/statue, receiving and sending messages | ✅ |
| The mobile application must be able to switch the context of the questions/answers according to the mentor choice | ⚠️ |
| The interaction between the mobile application and the backend must be safe and guarantee the privacy of the user | ⚠️ |
| The interaction between the mobile application and the backend must guarantee predictable behavior in case of failures or critical situations | ✅ |
| The interaction between the mobile application and the backend must guarantee correct behavior in case of unexpected input or situation | ⚠️ |
| The mobile application must be able to guarantee the login on the application | ⚠️ |
| The interaction between the mobile application and the backend must be flexible so that fixes, upgrade and new development can be easily implemented | ✅ |
| The user should be able to choose and change the mentor, so the application must be able to communicate that operation to the backend | ⚠️ |
| The mobile application must be able to interact with the user with a chatbot | ⚠️ |
| The mobile application must be able to serve three types of mentor, simple, advanced and english mentor | ⚠️ |
| The chatbot must be a finite-state automaton | ⚠️ |

#### Database - BackEnd
| Feature | Status |
| :---- | :----: |
| The backend must be able to interact with the database through a query system, in particular, all the information on the database must be retrieved and eventually updated or deleted. | ✅ |
| The database should be reachable in every moment, in case of a fault the system must be able to control the situation. | ✅ |
| Eventually sensible data must be encrypted by the backend before the insertion. | ✅ |
| The interaction between the database and the backend must be able to guarantee backup services and disaster recovery procedures. | ⚠️ |
| The interaction between the database and the backend must guarantee the consistency of the information stored. | ✅ |

#### Dashboard - BackEnd
| Feature | Status |
| :---- | :----: |
| The dashboard must be able to send a request to and receive a response from the back-end via HTTP | ⚠️ |
| The dashboard must be able to insert/delete works of arts, interacting with the back-end | ⚠️ |
| The dashboard must be able to edit works of arts, interacting with the back-end | ⚠️ |
| The dashboard must be able to edit questions and answers for the works of art, interacting with the back-end | ⚠️ |
| The dashboard must be able to display most frequently asked question to the museum | ⚠️ |
| The dashboard must be able to display most voted statues to the museum | ⚠️ |
| The dashboard must be able to display most liked answers to the museum | ⚠️ |

#### Google Cloud Platform - BackEnd
| Feature | Status |
| :---- | :----: |
| The BackEnd must be able to establish a connection with google cloud platform | ✅ |
| The BackEnd must be able to describe the topic referred to the sensors failures detection | ✅ |

#### Embedded system
| Feature | Status |
| :---- | :----: |
| The STM32 nucleo board must be able to interact with the X-NUCLEO-IDB05A1 expansion board (Bluetooth) | ⚠️ |
| The STM32 nucleo board must be able to interact with the X-NUCLEO-IDW01M1 expansion board (Wifi) | ✅ |
| The STM32 nucleo board must be able to interact with the X-NUCLEO-IKS01A2 expansion board (sensors) | ⚠️ |
| The Nucleo board must be able to establish a wifi connection | ✅ |
| The Nucleo board must be able to send values through an MQTT connection | ⚠️ |
| The Nucleo board must be able to broadcast and accept BLE packets | ⚠️ |
| The Nucleo board must be visible by the mobile devices | ⚠️ |

#### User activity/emotion recognition - Music Generation
| Feature | Status |
| :---- | :----: |
| The database must be able to collect data from the sensor associated with the user | ⚠️ |
| The system must be able to collect the most frequently asked questions | ⚠️ |
| The system must be able to collect the total application usage time | ⚠️ |
| The system must be able to collect the time spent with the statue the user interacted most | ⚠️ |
| The system must be able to convert the scientific data to musical notes | ⚠️ |
| The BackEnd must be able to send the data to the Neural Network uploaded on GCP | ⚠️ |
| Based on the musical notes, the Neural Network must be able to generate a melody | ⚠️ |
| The database must be able to purge data at the end of the visit | ⚠️ |

***PoC***: means that the functionality is simulated

---
## <a id="comp"></a>Competitors
In this table, we try to compare Ablativo with some of the applications already present in the world. In particular as competitors we have chosen:
- [First Romanian School](https://play.google.com/store/apps/details?id=com.first.romanianschool)
- [AMI Filangieri Smart Museum](https://play.google.com/store/apps/details?id=it.naosconsulting.ami&hl=it)
- [FluxGuide](https://www.fluxguide.com/en/)

Features | Ablativo | FRSchool | AMI | FluxGuide | 
|----|:----:|:----:|:----:|:----:|
Interaction with statues | ✅ | ✅ | ✅ | ✅
Activity/Emotion recognition | ✅ | ❌ | ❌ | ❌ 
Music Generation | ✅ | ❌ | ❌ | ❌ 
Chatbot to know specific features | ✅ | ❌ | ❌ | ❌ 
Mentor | ✅ | ❌ | ❌ | ❌
Different visit according to user's competence | ✅ | ❌ | ❌ | ❌
Multiple language visits | ✅ | ✅ | ✅ | ✅
Data Analysis for museums | ✅ | ❌ | ✅ | ❌
Complete description of statues | ❌| ✅ | ✅ | ✅
Voice messages | ✅ | ❌ | ✅ | ❌
Audio guide | ❌ | ✅ | ✅ | ✅
Video guide | ❌ | ❌ | ❌ | ✅
Augmented Reality | ❌ | ❌ | ❌ | ❌
3D modeling | ❌ | ❌ | ❌ | ✅
Possibility of making treasure hunts | ✅ | ❌ | ✅ | ❌
Available to every museums | ✅ | ❌ | ❌ | ✅

---
## Previous versions

* [Evaluation - delivery 1](https://github.com/Ablativo/ablativo/blob/1st-delivery/Evaluation.md)