# Service Contract

FidesInnova introduces a groundbreaking feature – FidesInnova Service Contracts. Service Contracts are scripts designed to encode business logic between IoT devices, enabling them to communicate and share data without a central authority. These contracts perform the same functions as Smart Contracts, specifically within the decentralized IoT domain. Executed through FidesInnova Blockchain Nodes, Service Contracts leverage a Virtual Machine capable of running JavaScript. This functionality enables the creation and execution of intricate interactions between IoT devices and users, thereby enhancing adaptability and functionality within the blockchain.

### **How to use** FidesInnova **Service Contracts?**

**1. FidesInnova Mobile App:** FidesInnova Service Market is a hub of diverse services accessible through the FidesInnova Mobile App. It provides users with a variety of prewritten services to explore and implement based on their needs. These contracts enhance IoT device capabilities by automating data exchanges. More advanced users who want to create their own services can use the FidesInnova Web App to write a new service and share it with others in the FidesInnova Service Market.

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

**2. FidesInnova Web App:** FidesInnova Web App offers a versatile platform for a dynamic programming environment for creating Service Contracts. The FidesInnova Web App empowers users to develop automated solutions for data exchange between devices and users.

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="563"><figcaption></figcaption></figure>

**– Visual and Text-Based Development:** The FidesInnova Web App accommodates novice and experienced developers at the same time, allowing code creation through Blockly or JavaScript. The Visual Console, utilizing Blockly, offers a graphical development console, while the Coding Console, based on JavaScript syntax, caters to traditional coding methods.

<figure><img src="https://fidesinnova.io/wp-content/uploads/2023/12/blockly-p-1024x422.png" alt="" width="563"><figcaption></figcaption></figure>

**– Community Collaboration:** The FidesInnova Web App promotes the sharing and collaboration of Service Contracts within the FidesInnova community, fostering an environment of innovation and collective growth. Moreover, the Service Creator feature enables the monetization of various data types, promoting income generation by sharing data.

### **Example of** FidesInnova **Service Contracts in Action:**

– Temperature Sensors: Utilizing the Service Creator within the FidesInnova Web App, users can create a weather map based on living environment data. By selling this data to customers, weather data and Service Contracts can be monetized, showcasing the practical and commercial potential of the FidesInnova ecosystem in leveraging IoT data.

### **Technical details:**

Isolated-vm Integration: FidesInnova employs isolated-vm to execute Service Contracts, isolating them from the FidesFidesInnova Blockchain Node. It prevents errors or resource leaks in service contracts from affecting the overall system, ensuring optimal performance.

\
Multiple Isolated Contexts: FidesInnova will create multiple isolated contexts within a single Node.js process to mitigate the risk of runaway code consuming excessive resources. This approach allows for the independent execution from multiple instances of a Service Contract to enhance system stability.
