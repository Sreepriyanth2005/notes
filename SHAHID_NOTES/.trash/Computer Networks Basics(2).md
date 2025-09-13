
**Computer networking** is the practice of connecting multiple computing devices (such as computers, servers, printers, and smartphones) to share resources, exchange data, and communicate with each other. These connections can be established using wired or wireless methods.

### What is the **Web** (World Wide Web)?

The **Web**, or **World Wide Web (WWW)**, is a **system of interlinked web pages and resources** accessed via the internet. It uses **web browsers** (like Chrome, Firefox, or Safari) to display information in the form of websites.

It works using:
- **HTTP/HTTPS protocols** (rules for data transfer)
- **URLs** (addresses for web resources)
- **HTML/CSS/JavaScript** (to build and style content)

### What is the **Internet**?

The **Internet** is a **global network of interconnected computers and devices** that communicate with each other. It’s the **infrastructure** that supports not only the Web but also **email**, **file transfer**, **online gaming**, **video conferencing**, and more.   

|Feature|**Web (WWW)**|**Internet**|
|---|---|---|
|**Definition**|A system of web pages and content linked by hyperlinks|A massive network connecting millions of computers|
|**Function**|Delivers documents, images, videos via browsers|Transfers all types of data (web, email, files, etc.)|
|**Access**|Accessed using web browsers|Accessed using various applications (browser, email, FTP, etc.)|
|**Depends On**|Runs on top of the internet|Fundamental infrastructure|
|**Examples**|Websites like Google, YouTube, Wikipedia|Services like email, online games, cloud stora|

### Network

A **network** is a collection of **two or more computers/devices** connected together so they can **communicate, share resources, and exchange data**.

- **Nodes (Devices)** → Computers, smartphones, printers, servers, routers.
- **Links (Channels)** → Cables (Ethernet, fiber) or wireless signals (WiFi, Bluetooth).
- **Protocols** → Rules for communication (like TCP/IP, HTTP, FTP).

**Why ?**
- **Share resources** → printers, files, internet connection.
- **Communicate** → email, video calls, messaging.
- **Collaboration** → multiple users working on shared data.
- **Remote access** → access files or systems from anywhere.
### Types of Networks

1. **LAN (Local Area Network)**
	- A network that covers a **small geographical area** such as a single building, office, or school.
	- Managed by a single organization.
	- Eg : A **computer lab** in a college.

2. **MAN (Metropolitan Area Network)**
	- A network that covers a **city or large campus**. Larger than LAN but smaller than WAN.
	- Spans **10–50 km**,Often used to connect multiple LANs within a city.
	- Eg : **Cable TV networks** in a city.

3. **WAN (Wide Area Network)**
	- A network that covers a **very large geographical area**, even worldwide.
	- Spans countries or continents.
	- Eg : **MNC companies** connecting their offices in different countries.
	
4. **PAN (Personal Area Network)
    - A network for **personal devices** within a very short range (about 10 meters).	
    - Used by an individual for connecting personal devices.
    - Eg : **Bluetooth** connection between phone and wireless earphones.

5. **WLAN (Wireless Local Area Network)**
	- A type of **LAN that uses wireless technology** (WiFi) instead of cables.
	- Devices connect through WiFi access points (router).
	- Eg: **Home WiFi** networks.


### Topology

##### Point to Point Topology

Point-to-point topology is a type of topology that works on the functionality of the sender and receiver. It is the simplest communication between two nodes, in which one is the sender and the other one is the receiver. Point-to-Point provides high bandwidth.

![Point-to-point-topology|500](https://media.geeksforgeeks.org/wp-content/uploads/20240614235231/Point-to-point-topology.png)

Point to Point Topology

##### Mesh Topology

In a mesh topology, every device is connected to another device via a particular channel. Every device is connected to another via dedicated channels. These channels are known as links. In Mesh Topology, the protocols used are AHCP (Ad Hoc Configuration Protocols), [DHCP](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/) (Dynamic Host Configuration Protocol), etc.

![Mesh-Topology|500](https://media.geeksforgeeks.org/wp-content/uploads/20241028174648312121/Mesh-Topology-660.png)


##### Star Topology

In Star Topology, all the devices are connected to a single hub through a cable. This hub is the central node and all other nodes are connected to the central node.

![[Pasted image 20250523211725.png|500]]

##### Bus Topology

Bus Topology is a network type in which every computer and network device is connected to a single cable. It is bi-directional.

![[Pasted image 20250523211743.png]]

##### Ring Topology

In a Ring Topology, it forms a ring connecting devices with exactly two neighboring devices.The data flows in one direction, i.e. it is unidirectional.

![[Pasted image 20250523211821.jpg|500]]

##### Tree Topology

Tree topology is the variation of the Star topology. This topology has a hierarchical flow of data. In Tree Topology, protocols like [DHCP](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/) and ****SAC (Standard Automatic Configuration)**** are used.

![Tree-topology|500](https://media.geeksforgeeks.org/wp-content/uploads/20240614234036/Tree-topology-660.png)


##### Hybrid Topology

Hybrid Topology is the combination of all the various types of topologies

![[Pasted image 20250523211939.png|500]]

### What is Transmission Modes?

- Transmission mode means transferring data between two devices. It is also known as a communication mode.
- how data flows between two connected devices.

##### Simplex Mode

In Simplex mode, the communication is unidirectional, as on a one-way street. Only one of the two devices on a link can transmit, the other can only receive.

Eg : Keyboard

![[Pasted image 20250523212549.png]]

##### Half-Duplex Mode

In [half-duplex mode](https://www.geeksforgeeks.org/difference-between-half-duplex-transmission-modes-and-full-duplex-transmission-modes/), each station can both transmit and receive, but not at the same time. When one device is sending, the other can only receive, and vice versa

Eg : Walkie Talkie

![[Pasted image 20250523212650.png]]

##### Full-Duplex Mode

In full-duplex mode, both stations can transmit and receive simultaneously.
Eg: Normal Phone calls

![[Pasted image 20250523212745.png]]

### Switching

- In **computer networks**, **switching** is the process of forwarding data from one device to another across a network.
- **how data travels** from the **source to the destination** using the best possible path.

##### Circuit Switching

- A **dedicated physical path** is established between sender and receiver before communication begins.
- Once the connection is set, all data travels through the same path.
- Advantages : Guaranteed bandwidth, no delay once the circuit is set
- Disadvantages : Wastes resources if no data is transmitted (path remains reserved).

**Real world Example**

- Traditional landline telephone systems are the **classic example of circuit switching**.
- When you dial a number, the telephone exchange establishes a **dedicated path (circuit)** between caller and receiver.
- This circuit remains **reserved until the call ends**, even if you are silent.

##### Packet Switching

- Data is broken into **small packets**.
- Each packet may take **different routes** to reach the destination.
- At the destination, packets are reassembled into the original message.
- Advantages: Efficient use of network, supports many users.
- Disadvantages: Packets may be delayed, arrive out of order, or get lost

**Real world Example**

- When you open a website (e.g., `www.youtube.com`), the data (HTML, CSS, video, etc.) is broken into **packets**.
- Each packet may travel through **different routers** and paths.
- At your computer, the packets are **reassembled** into the complete page or video.

##### Message Switching 

- In **message switching**, the **entire message** (not small packets) is treated as **one single unit of data**.
- The message travels from one switch (node) to another using the **store-and-forward technique**.

**Store-and-forward**

- When a full **message** arrives at a switch, the switch **stores the entire message temporarily**.
- The switch then **forwards the whole message** to the next switch on the path toward the destination.
- This continues until the message reaches the final receiver.

**Real world Example**

- When you send an email, the entire email (with attachments) can be stored on intermediate mail servers before being forwarded.

