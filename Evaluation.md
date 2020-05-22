# Evaluation
This document aims to provide details on how to evaluate the product, first from a user experience point of view, and then from a technical point of view.

## User experience
To first evaluate the idea, we have used a survey, sharing it with our family, friends, and friends of friends. Indeed, by these feedbacks and suggestions, we (hopefully) understood where to make some changes, and especially if the final user would really like and possibly use the final service.

Here the anonymous results:
- [International](https://docs.google.com/spreadsheets/d/15IgMSvd-63VwI2cXw7SHC1U36O2IEgHQvG_yR56Y7Nk/edit#gid=675511585)
- [Italian](https://docs.google.com/spreadsheets/d/1EfuZT_q8hNwSY7gu_bXCDNayzk7qYUeNwSBV3rvE9xY/edit#gid=510814664)

Here the most relevant graphs:
- [International](./pdf/graph_international.pdf)
- [Italian](./pdf/graph_Italy.pdf)


We received more than 100 replies from Italian people, and more than 40 from people spread over 15 different countries.

Over 90% of them believe this service would be useful to improve the learning of the fundamental characteristics of a work of art, help the museum to provide a better service, boost their curiosity, and would have fun trying the application.
The same percentage of people would go to the museum to try the novelty, however, in Italy, only around 50% if they have already been there, while in the other countries this percentage increases to ~65%.
Finally, over 80% of these people told us they are thinking to download for real our application on their smartphone.

Now, let's define the parameters we will use for the final evaluation:
- The museum visitor can easily sign-in/sign-up and choose his/her mentor;
- The museum visitor can easily interact with the mentor, which will have as natural as possible human-like behavior;
- The museum visitor will correctly receive messages from a work of art while standing close to it;
- The interaction between the mentor and the works of art will seem as natural as possible;
- The museum owner can easily understand the metrics collected by the service;

## Technical aspects
Another face of the same coin, a technical evaluation is a fundamental step of our work. Ablativo is made of five different components that needs to fully interact eachother.

#### Mobile application <---> Beacon sensor
1. The beacon must be able to broadcast and accept BLE packets
2. The beacon must be visible by the mobile devices 
3. The mobile device must be able to broadcast and accept BLE packets
4. The mobile device must be able to read the UUID of the beacon it interacts with
5. If the user moves away, the mobile device must be able to understand that it is no longer near the work of art

#### Mobile-Application <---> BackEnd
1. The mobile application must be able to send request to and receive response from the back-end via HTTP through fetch construct.
2. The mobile application must be able to interact with the backend in order to estabilish a dialog between the user and the mentor/statue, receiving and sending messages.
3. The interaction between the mobile application and the backend must be safe and guarantee the privacy of the user.
4. The interaction between the mobile application and the backend must guarantee a predictable behaviour in case of failures or critical situation.
5. The interaction between the mobile application and the backend must guarantee a correct behaviour in case of unexpected input or situation.
6. The mobile application must be able to guarantee the login on the application.
7. The interaction between the mobile application and the backend must be flexible so that fixes, upgrade and new development can be easily implemented.
8. The user should be able to choose and change the mentor, so the application must be able to comunicate that operation to the backend.

#### Database <---> BackEnd
1. The database must be able to interact with the database through a query system, in particular all the information on the database must be retrieved and eventually updated or deleted.
2. The database should be reachable in every moment, in case of fault the system must be able to control the situation.
3. Eventually sensible data must be encrypted by the backend before the insertion.
4. The interaction between the database and the backend must be able to guarantee backup services and disaster recovery procedures.
5. The interaction between the database and the backend must guarantee the consistency of the information stored.

#### Dashboard <---> BackEnd
1. The dashboard must be able to send request to and receive response from the back-end via HTTP
2. The dashboard must be able to insert/delete works of arts, interacting with the back-end
3. The dashboard must be able to edit works of arts, interacting with the back-end
4. The dashboard must be able to edit questions and answers for the works of art, interacting with the back-end
5. The dashboard must be able to display diagnostic results to the museum
