# Evaluation
This document aims to provide details on how to evaluate the product, first from a user experience point of view, and then from a technical point of view.

<img src="./img/kpi.png" width="600" />

We based our evaluation model in the well known **Key Performance Indicators**. The generic identikit of the KPIs must meet certain characteristics: the indicators must be ***quantifiable*** (and therefore measurable); ***management***, i.e. they must indicate whether the company is growing or not; ***operational***, and therefore exercise an effective change in the strategy adopted; finally ***practical***, and therefore adaptable to business needs.

---
### Table of contents
[User experience](#usex)
[Technical aspects](#tech)
[Components interactions](#inter)
[Competitors](#comp)

---
## <a id="usex"></a>User experience

#### Users feedbacks
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
    * The museum visitor can easily interact with the stautes, which will have as natural as possible human-like behavior
    * The museum curator can easily understand and see the statistics of the metrics collected by the service
* **Usability**: The response times of the chat must be rapid otherwise this could lead the user to not use it
* **Graphic interface**: The interaction between the mentor and the works of art will seem as natural as possible. The overall interface must be user friendly.
* **Privacy & Security**: Ablativo doesn't store any type of sensible data, the passwords will be encrypted.
---
## <a id="tech"></a>Technical aspects
Technical evaluation is a fundamental step in our work. We based our analysis on some specific metrics: `Accessibility`, `Accuracy`, `Complexity`, `Robustness`, `Cost`, `Scalability`, `Security`. Together with these, depending on the component taken into consideration, there will be some more specific characteristics.

* ⚠️ Work in progress
* ✅ Completed

### Beacon STM32
##### Metrics description
* **Accessibility**: indicates the ability of the technology to be exploited by the user.
* **Radius**: refers to the distance at which the signal is transmitted and received.
* **Accuracy**: TODO
* **Precision**: precision considers how the system works overtime, how similar the various measurements are to each other, which does not necessarily mean that the system is accurate.
* **Complexity**: complexity can be attributed to hardware, software needed for the system
* **Robustness**: the system's ability to resist interference and noise from nearby sensors
* **Scalability**: the scalability of a system ensures its normal operation even when the sphere of the application becomes larger.
* **Cost**: the cost of a system like this can depend on several factors. The most important ones include money, time, space, weight, and energy. The time factor is linked to installation and maintenance times.
* **Security**: security means the danger that data sent through the system will be violated or accessed by third parties.
* **Failure detection**: the system must be able to notify the museum if there is a fault.

##### Metrics evaluation
| Metrics | Status |Solution/Result |
| ------------- |---| :-----|
| `Accessibility` | ✅ | Battery-powered that can last up to 2 years, they can be placed on any surface, accessible from the mobile app |
| `Radius` | ⚠️ |
| `Accuracy` | ⚠️ |
| `Precision` | ⚠️ |
| `Complexity` | ✅ | The architecture is very simple to install and to develop thanks to STM32 community specifications |
| `Robustness` | ⚠️ |
| `Scalability` | ⚠️ |
| `Cost` | ⚠️ | Cost of sensors + Cost of Google Cloud Platform |
| `Security` | ✅ | Beacons transmit output signals, there is no intrinsic safety risk in the transmission |
| `Failure detection` | ✅ | Being the statues close to each other, will be beacons (named guards) that monitor the other neighbors and report faults via the Google Cloud |

**NOTE**: we will be able to do some measures only when we have the sensors in the hand.

### Mobile app
##### Metrics description
* **Accessibility**: indicates the ability of the technology to be exploited by the user.
* **Accuracy**: average error in calculating the distance from the statues.
* **Precision**: how the system works overtime, how similar the various measurements are to each other, which does not necessarily mean that the system is accurate.
* **Complexity**: complexity can be attributed to hardware, software needed for the system.
* **Robustness**: the system's ability to resist interference and noise from nearby mobile devices.
* **Scalability**: the scalability of a system ensures its normal operation even when the sphere of the application becomes larger.
* **Cost**: the cost of a system like this can depend on several factors. The most important ones include money, time, space, weight, and energy.
* **Security**: security means the danger that data sent through the system will be violated or accessed by third parties.

##### Metrics evaluation
| Metrics | Status |Solution/Result |
| ------------- | ---| :----- |
| `Accessibility` | ✅ | Accessible with a simple smartphone |
| `Accuracy` | ⚠️ | Calculated as the average of the Euclidean distance between the estimated and the real position |
| `Precision` | ⚠️ | Comparison of the various measurements |
| `Complexity` | ✅ | Thanks to the framework React native the implementation is very simple and fast |
| `Robustness` | ✅ | Multiple requests by the nearby statues are managed by the backend and in case of indecision on what statue are the closest, we will ask the user with which wants to talk |
| `Scalability` | ✅ | Being designed for an internal museum, it will have a number of connected users that will never be too high to affect scalability |
| `Cost` | ✅ | In the future to handle big amount of data MongoDB could be a cost (not for the initial setup) |
| `Security` | ✅ | All data provided by the users will be encrypted. No sensible data are needed |

**NOTE**: we will be able to do some measures only when we have the sensors in the hand.

---
## <a id="inter"></a>Components interactions
Ablativo is made of five different components that need to fully interact with each other. These interactions must be well defined.
* ⚠️ Work in progress
* ✅ Completed
#### 1. Mobile application - Beacon sensor
| Feature | Status |
| :---- | ---- |
| The beacon must be able to broadcast and accept BLE packets | ⚠️ |
| The beacon must be visible by the mobile devices | ⚠️ |
| The mobile device must be able to broadcast and accept BLE packets | ⚠️ |
| The mobile device must be able to read the UUID of the beacon it interacts with | ⚠️ |
| If the user moves away, the mobile device must be able to understand that it is no longer near the work of art | ⚠️ |

#### 2. Mobile-Application - BackEnd
| Feature | Status |
| :---- | ---- |
| The mobile application must be able to send the request to and receive a response from the back-end via HTTP through fetch construct | ⚠️ |
| The mobile application must be able to interact with the backend to establish a dialog between the user and the mentor/statue, receiving and sending messages | ⚠️ |
| The mobile application must be able to switch the context of the questions/answers according to the mentor choice | ⚠️ |
| The interaction between the mobile application and the backend must be safe and guarantee the privacy of the user | ⚠️ |
| The interaction between the mobile application and the backend must guarantee predictable behavior in case of failures or critical situations | ⚠️ |
| The interaction between the mobile application and the backend must guarantee correct behavior in case of unexpected input or situation | ⚠️ |
| The mobile application must be able to guarantee the login on the application | ⚠️ |
| The interaction between the mobile application and the backend must be flexible so that fixes, upgrade and new development can be easily implemented | ⚠️ |
| The user should be able to choose and change the mentor, so the application must be able to communicate that operation to the backend | ⚠️ |

#### 3. Database - BackEnd
| Feature | Status |
| :---- | ---- |
| The backend must be able to interact with the database through a query system, in particular, all the information on the database must be retrieved and eventually updated or deleted. | ⚠️ |
| The database should be reachable in every moment, in case of a fault the system must be able to control the situation. | ⚠️ |
| Eventually sensible data must be encrypted by the backend before the insertion. | ⚠️ |
| The interaction between the database and the backend must be able to guarantee backup services and disaster recovery procedures. | ⚠️ |
| The interaction between the database and the backend must guarantee the consistency of the information stored. | ⚠️ |

#### 4. Dashboard - BackEnd
| Feature | Status |
| :---- | ---- |
| The dashboard must be able to send a request to and receive a response from the back-end via HTTP | ⚠️ |
| The dashboard must be able to insert/delete works of arts, interacting with the back-end | ⚠️ |
| The dashboard must be able to edit works of arts, interacting with the back-end | ⚠️ |
| The dashboard must be able to edit questions and answers for the works of art, interacting with the back-end | ⚠️ |
| The dashboard must be able to display most frequently asked question to the museum | ⚠️ |
| The dashboard must be able to display most voted statues to the museum | ⚠️ |
| The dashboard must be able to display most liked answers to the museum | ⚠️ |

**NOTE**: All these interactions are work in progress, we will update the status of these tables according to the development process. 

---
## <a id="comp"></a>Competitors
In this table, we try to compare Ablativo with some of the applications already present in the world. In particular as competitors we have chosen:
- [First Romanian School](https://play.google.com/store/apps/details?id=com.first.romanianschool)
- [AMI Filangieri Smart Museum](https://play.google.com/store/apps/details?id=it.naosconsulting.ami&hl=it)
- [FluxGuide](https://www.fluxguide.com/en/)

Features | Ablativo | FRSchool | AMI | FluxGuide | 
|----|----|----|----|----|
Interaction with statues | ✅ | ✅ | ✅ | ✅
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