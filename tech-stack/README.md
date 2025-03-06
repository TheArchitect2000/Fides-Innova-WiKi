# Tech Stack



<figure><img src="../.gitbook/assets/image (3).png" alt="" width="563"><figcaption></figcaption></figure>

### Scenario 1

This setup enables the seamless transfer of IoT Sensors data and funds between two distinct nodes. The depicted steps illustrate the blockchain communication and Fides data transfer workflow. The process begins with the presumption that the Data Consumer installed a Service Contract and uses an IoT Sensor from the Shared Devices List. Following this, the Data Consumer kick-starts the process by depositing a sufficient amount of tokens, thus establishing a dedicated fund for the data transactions.\
\
0\) Presumptions: The Data Producer in Node X shares IoT Sensor A. The device ID gets added to the Shared Devices List on the Blockchain, and a Smart Contract is created automatically for the device.\
A Data Consumer from Node Y installs a Service and selects IoT Sensor A from the Shared Devices List.\
The Service Contract is initiated at Node Y.\
IoT Sensor A sends data to the MQTT broker in node X. Then it is stored in the data storage.

1. The Data Consumer deposits sufficient funds into the IoT Sensor A Smart Contract. Additionally, it provides a key to the Smart Contract for release fund purposes.
2. The Service Contract requests and retrieves the node and IoT Sensor A ID from the Shared Devices List on the Blockchain.
3. The Service Contract establishes an MQTT connection between the Service Contract on Node Y and the MQTT broker on Node X.
4. The Service Contract receives IoT Sensor A’s data from the MQTT broker.
5. If the set condition of the Service Contract is correct, the Service Contract sends a notification to the Data Consumer.
6. The Service Contract on Node Y sends a release funds request to the IoT Sensor A Smart Contract. The Smart Contract utilizes the provided key to release funds.
7. The Data Producer requests a withdrawal from the Smart Contract and will receive the payment in their wallet.

### Scenario 2

This setup enables the seamless transfer of IoT Sensors data and funds between two distinct nodes. The depicted steps illustrate the blockchain communication and Fides data transfer workflow. The process begins with the presumption that the Data Consumer installed a Service Contract and uses an IoT Sensor from the Shared Devices List. Following this, the Data Consumer kick-starts the process by depositing a sufficient amount of tokens, thus establishing a dedicated fund for the data transactions.\
0\) Presumptions:\
The Data Producer in Node X shares IoT Sensor A. The device ID gets added to the Shared Devices List on the Blockchain, and a Smart Contract is created automatically for the device.\
A Data Consumer from Node Y installs a Service and selects IoT Sensor A from the Shared Devices List.\
The Service Contract is initiated at Node Y.\
IoT Sensor A sends data to the MQTT broker in node X. Then it is stored in the data storage.

1. The Data Consumer deposits sufficient funds into the IoT Sensor A Smart Contract. Additionally, it provides a key to the Smart Contract for release fund purposes.
2. The Service Contract requests and retrieves the node and IoT Sensor A ID from the Shared Devices List on the Blockchain.
3. The Service Contract establishes an MQTT connection between the Service Contract on Node Y and the MQTT broker on Node X.
4. The Service Contract receives IoT Sensor A’s data from the MQTT broker.
5. If the set condition of the Service Contract is correct, the Service Contract chages the state of IoT Actuator B.
6. The Service Contract on Node Y sends a release funds request to the IoT Sensor A Smart Contract. The Smart Contract utilizes the provided key to release funds.
7. The Data Producer requests a withdrawal from the Smart Contract and will receive the payment in their wallet.
