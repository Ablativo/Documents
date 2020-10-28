# 3rd Delivery

### FeedBack of 2nd Delivery

* **PROS**:
  * ✅ Good job with respect to the previous delivery. The cons are managed in the right way 

* **CONS**:

  * ❌ Evaluation is good but it must be more specific
  * ❌ Improve the flow of the presentation

### Design, Architecture, and Evaluation updates

* **DESIGN**: there were no changes in the design

[Design document](./Design.md)

<br>

* **ARCHITECTURE**:

 1. Switched from Google Cloud Platform to `AWS` services due to the fact that our board is not able to interact with GCP.
 2. Added decription of AWS services used: `IoT Core`, `DynamoDB`, `EC2`, `Cognito`, `Amplify`
 3. Switched from MongoDB to DynamoDB to comply with the cloud infrastructure of AWS.
 4. Switched from Heroku to EC2 to comply with the cloud infrastructure of AWS.
 5. Choosed the `B-L475E-IOT01` board, given the higher reliability (More details on this choice are explained in the Architecture document)
 6. Removed `Ambient light sensor` because React is not able to interact with it very well
 7. Added description of the music generation with `Magenta` and `MusicRNN`

[Architecture document](./Architecture.md)

<br>

* **EVALUATION**:

1. Added cost analysis for AWS services
2. Added accuracy and precision for BLE
3. Updated functionalities implementation state to show the development state

[Evaluation document](./Evaluation.md)

### Functionalities implementantion state

* **3rd Delivery**: we switched all the infrastructure from Google Cloud Platform to Amazon Web Service, then we focused our development on the features specified in the previous delivery: 
  - Dashboard for curators
  - Mentor logic
  - real hardware sensors implementation
  - smartphone sensors
  - finite-state automaton to transform the chat in a chatbot
  - retrieve information about user activity
  - convert these data into musical notes and finally generate the melody with a Recurrent Neural Network

* **Future work**: 
  - Chatbot implemented with an artificial intelligence, such as [Amazon Lex](https://aws.amazon.com/it/lex/)
  - Different visit according to user's competence and language
  - Q&A with vocal messages 
  - Collect data referring to most frequently asked questions
  - Generate the music based not only on the activity but also with the emotion of users (User emotion recognition)

Detailed information about the functionalities implementantion state are available in [Evaluation document](./Evaluation.md#state)

### Evaluation (//TODO)
* **3rd Delivery**: 
* **Future work**:

Detailed information about the Evaluation are available in [Evaluation document](./Evaluation.md#costs)