# QuTech Challenges @ MIT iQuHACK 2022

<p align="left">
  <a href="https://qutech.nl" target="_blank"><img src="https://user-images.githubusercontent.com/10100490/151484481-7cedb7da-603e-43cc-890c-979fb66aeb60.png" width="25%" style="padding-right: 0%"/></a>
  <a href="https://iquhack.mit.edu/" target="_blank"><img src="https://user-images.githubusercontent.com/10100490/151647370-d161d5b5-119c-4db9-898e-cfb1745a8310.png" width="10%" style="padding-left: 0%"/> </a>
</p>




## Description of Quantum Key Distribution Protocol

Quantum Key Distribution (QKD) is a secure communication method which implements a cryptographic protocol involving components of quantum mechanics. It enables two parties  to produce a shared random secret key known only to them, which can then be used to encrypt and decrypt messages. It is often incorrectly called Quantum cryptography, as it is the best known example of such a task.

An important and unique property of QKD is the ability of the two communicating users to detect the presence of any third party interference trying to gain the knowledge f the key. By using quantum superpositions or quantum entanglement and transmitting information in quantum states , a communication system can be implemented that detects eavesdropping. 

Quantum computers with higher volume can be used to break RSA crypo-systems, a pillar on which most of today's banking encryption systems are based on. The proposed system can be used to carry out the transfer of payment from one user to another. As a further extension multi-user interface proposed can be used to carryout out multiple customer transactions at the same time.


   **PROPERTIES AND MERITS**:
   
   1. Relies on the principles of quantum mechanics in contrast to traditional public key cryptography which relies on cerain mathematical functions.
   2. QKD has provable security based on information theory , and forward secrecy.
      
   **DRAWBACKS**:
   
   1. It relies on having an authenticated classical channel of communications.
   2. In modern cryptography, having an authenticated class channel means that one has either already developed or exchanged a symmetric key of sufficient length. 
   3. Thus QKD does the work of a stream cipher at many times the cost.


<a href="https://qt.eu/discover-quantum/underlying-principles/quantum-key-distribution-qkd/" target="_blank"><img src="https://qt.eu//app/uploads/2018/11/qkd.jpg" width="75%" style="padding-left: 0%"/> </a>
## MQTT protocol
MQTT is an OASIS standard messaging protocol for the Internet of Things (IoT). It is designed as an extremely lightweight publish/subscribe messaging transport that is ideal for connecting remote devices with a small code footprint and minimal network bandwidth. MQTT today is used in a wide variety of industries, such as automotive, manufacturing, telecommunications, oil and gas, etc.(from https://mqtt.org/)

Therefore, we decide to use this protocol to implement the QKD .

## Implementation of Two user MQTT protocol and extension to multiuser.
<a target="_blank"><img src="https://cdn.mathpix.com/snip/images/GXEn2GxUTY8ZKxd8ovKnTPl0kJdDLhc_xRroZ8bTlZ4.original.fullsize.png" width="75%" style="padding-left: 0%"/> </a>

* User A and User B publish the basis they chose bases to the intermediate feed, and the interface as a subscriber to that feed will receive messages from them. 
* The intermediate interface can then generate the random initial state, which will then be sent to the Quantum Inspire.
* The measurement is done in the quantum inspire in the basis of user A and user B chosen by creating the quantum circuit with A as qubit 0 and B as qubit 1. 
* The result then be sent back to the intermediate interface. The interface then will publish the results for A and B to the Feed A and B respectively so that user A and user B only receive their one result.
* Then they can communicate with each other openly discussing the basis they chosen and the result they get.

If we expand this to multi-user,

<a  target="_blank"><img src="https://cdn.mathpix.com/snip/images/2lJuVsRsjnO1NgPZ_MFq1xsKlA5yiwh_cHkpTJPrzGM.original.fullsize.png" width="75%" style="padding-left: 0%"/> </a>

In order to expand the network from our system of two, one user will become the host, and for each user other than the host will develop a quantum key distribution between the host and themselves. Take the 5-users network as an example, if user 5 want to send the messages to others, he will first create a quantum key 15 with the host followed the first picture in the first page I drew . And information then is encrypted by this quantum key 15 and be sent to user 1 (host). After user 1 (host) decode the information, he will use the quantum key encrypting based on QK12, QK13, and QK14 and sent to user 2, 3, and 4 respectively. Other user can get the information by decoded based on their Quantum key.

## Coding part
There are two jupyter notebook in the src file. One is Sender.ipynb for user and one is  Intermediate_Interface.ipynb for the intermediate interface. If a user want to join the network they will use the sender file and one computer need to host and use the Intermediate_Interface.ipynb file. To be simple Sender.ipynb is for user to interact with the server and the Intermediate_Interface.ipynb create the key between the user by using MQTT protocol(Adafruit server).

## Personal Experience

**MIT iQuHACK 2022** was really a fun and extraordinary experience for our whole team. We got to know a plethora of things, learnt to work on new challenges and even expanded our professional network by getting to know individuals from various backgrounds. On the technical side, our team worked on the challenge involving Quantum Key Distribution. For most of us this was our first event where we had to create something unique from scratch by referring to a problem statement. After much brainstorming and referring to various resources we have come up with a solution to the challenge. Every member of our team has worked hard on this project and we hope that our solution is useful for a unique application. At the end we would like to thank the organizers and also the mentors along with the staff for making this a memorable event for us.


