---
description: 'FidesInnova Mesh IoT Network (MIoTN): A Revolution in Connectivity'
---

# Mesh IoT Network

MIoTN protocol development fixed the problems of traditional Wi-Fi connections. Traditionally, every IoT device (node) needed direct communication to the user’s router. It caused connection problems with scaling and deployment in large areas and required expensive Wi-Fi infrastructure.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

In a mesh network, each device functions as an endpoint and simultaneously as a relay, creating a dynamic and interconnected web of IoT devices. By leveraging this technology, the problem of Wi-Fi blind spots in network deployment, especially for large areas will be solved.

Fides MIoTN is a wireless communication network that uses Wi-Fi in STA-AP modes. In Fides MIoTN configuration, all nodes will search for nearby IoTs in the same Wi-Fi port as the user’s router. Organized nodes in mesh topology can self-form and self-heal their network. It makes it particularly well-suited for the decentralized nature of IoT applications.

**Key Characteristics of Fides Mesh IoT Network:**

**1- Self-Healing Topology:** In traditional networks, the failure of a central hub can disrupt the entire system. Fides MIoTN, however, are resilient and self-healing. The root node will broadcast a message every 3 seconds to the whole network and declare its status. It will guarantee if one node fails, the network can autonomously and quickly detect the failure point and reroute communication through alternative paths, ensuring continuous connectivity.

**2- Scalability:** Mesh networks are highly scalable. As new devices join the network, they seamlessly integrate without a central management authority. This scalability makes mesh networks ideal for IoT applications, where the number of connected devices can vary dynamically. Fides MIoTN topology can support up to 1000 nodes and can scale up to 6 layers of IoT devices.

**3- Redundancy and Reliability:** The redundant paths in a mesh network enhance reliability. Even if one communication route is compromised, Fides IoT devices can find alternative paths to maintain connectivity. This redundancy is crucial for applications that demand high reliability and uptime.

To create the mesh network, we incorporate the painlessMesh library. It is a true ad-hoc network, meaning that no planning, central controller, or router is required. Any system of one or more nodes will self-organize into a fully functional mesh. The maximum size of the mesh is limited by the amount of memory in the heap that can be allocated to the sub-connections buffer.

<figure><img src="../../.gitbook/assets/image (39).png" alt="" width="563"><figcaption></figcaption></figure>

Fig 1 demonstrates all possible node statuses. In a mesh, one device will connect to the Wi-Fi router and become the Root, acting as a bridge between the mesh network and MQTT broker. A Parent Node is a device that connects to another node in the mesh and also serves as an intermediary for other nodes. A Leaf Node is always at the end of hops, or there are no devices connected to them. Additionally, if a device can’t find any mesh or router nearby, it will be an Idle Node, constantly searching and trying to find a mesh network or router to connect to.

Fides MIoTN added few new feature to the painlessMesh that was missing from the library. In Fides MIoTN, instead of hardcoding a status (Root/Node) in the code and then programming the device, devices can autonomously change their status to Node or Root by searching their surrounding area and looking for a mesh network or Wi-Fi router. This feature enables every device to change its state based on the required status. For example, if only one device is near the router, it will select the role of Root automatically, and other devices, by searching, can find that there is an active mesh network nearby, and they will all change their state to Node and form a mesh.

To ensure that the Root device has access to the internet and MQTT broker, every few seconds it will broadcast a message to the whole mesh network. If the Root device loses its connection to the Router or MQTT broker, it switches its own state to Node and lets another Node take its place and become Root. The first Node that can connect to the Router and the MQTT broker will be the new Root and broadcast its state to the mesh. In a case where a new device connects to the router and finds a Root device already existing on the same network, it starts a search for a nearby mesh network. If it can find one, it will instantly switch back to Node and form a mesh with the Root device. But if it can’t find the mesh network, it means that it is not in the signal range of any device, and instead of switching to Node, it will remain Root and start its own mesh network.
