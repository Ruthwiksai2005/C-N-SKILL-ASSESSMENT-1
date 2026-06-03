# RTS OF PURE AND SLOTTED ALOHA

## Student Details

| Field | Details |
|---------|---------|
| Name | RUTHWIK SAI R |
| Register No. | 212223060233 |
| Department | Electronics and Communication Engineering |
| Subject Code | 19EC412 |
| Subject Name | Communication Networks |
| Slot | T2-T22 |
| Submission Date | 16/05/2026 |

---

# Introduction
The ALOHA protocol, pioneered at the University of Hawaii in the early 1970s, remains a foundational concept in wireless communication and random-access networking. This report provides an exhaustive analysis of the two primary iterations—Pure ALOHA and Slotted ALOHA—with a specific focus on their real-time implementations in modern technology. By examining efficiency metrics, synchronization requirements, and real-world deployment across IoT, satellite, and cellular networks, we illustrate how these protocols balance simplicity with performance.

---

# Foundational Concepts and Theoretical Limits
At their core, ALOHA protocols allow multiple users to share a single communication channel without a central controller managing every transmission.

---
# Pure ALOHA
Pure ALOHA is the simplest form of random access. A station transmits a frame whenever it has data ready. If a collision occurs (detected by the absence of an acknowledgment), the station waits for a random period and tries again.
•	Efficiency: The maximum throughput is approximately 18.4%.
•	Vulnerability: A frame is vulnerable to collision for a period equal to twice its transmission time ($2 \times L$), as any transmission starting shortly before or during its window will cause a conflict.

---
# Slotted ALOHA
To double the efficiency of the channel, Slotted ALOHA discretizes time into specific slots equal to the frame duration.
•	Mechanism: Stations are only permitted to transmit at the beginning of a time slot.
•	Efficiency: This synchronization reduces the vulnerability window to a single slot ($1 \times L$), increasing maximum efficiency to 36.8%.

---
# Detailed Real-Time Scenarios: Pure ALOHA
Pure ALOHA thrives in environments where keeping power consumption extremely low or maintaining simplicity is more important than achieving high data throughput.

---
# LoRaWAN (Low Power Wide Area Network) Uplink
LoRaWAN is the backbone of many "Smart City" and industrial IoT applications.
•	Implementation: In the uplink (device-to-gateway) communication, IoT sensors often use a Pure ALOHA mechanism.
•	Why it's used: IoT devices, such as soil moisture sensors or smart parking meters, are often battery-powered and stay in sleep mode for long periods. Waiting for a specific "slot" would require the device to keep its internal clock perfectly synchronized with a central gateway, which consumes significant energy. By transmitting randomly when data is ready, these devices maximize battery life.

---
# Historical Satellite Communication
Originally, the ALOHA protocol was designed for satellite-based links connecting the Hawaiian Islands.
•	Implementation: Geographically dispersed stations transmitted data to a central satellite without a coordinator.
•	Why it's used: In the 1970s, the hardware required for complex slot synchronization over massive distances was cost-prohibitive. Pure ALOHA provided a functional, uncoordinated method for simple data exchange.
<img width="606" height="396" alt="image" src="https://github.com/user-attachments/assets/713c602e-2492-4fe8-8326-8cb0301e39b2" />

---
# Uncoordinated Tactical and Emergency Radio
In emergency or tactical scenarios, such as search-and-rescue operations in remote areas, infrastructure is often non-existent.
•	Implementation: Spontaneous radio networks allow units to broadcast status updates or GPS coordinates.
•	Why it's used: In these "ad-hoc" environments, there is no central timing mechanism available to establish slots. Pure ALOHA allows for immediate, uncoordinated transmission that is vital for spontaneous communication.
<img width="595" height="376" alt="image" src="https://github.com/user-attachments/assets/8b5a89d1-fe7e-481b-bf42-933beba77105" />

---

# Small Local Area Networks (LANs)
In very small, isolated LAN environments with minimal users.
•	Implementation: Simple wired or wireless setups with low traffic volume.
•	Why it's used: When the probability of two devices transmitting simultaneously is statistically negligible, the overhead of implementing Slotted ALOHA or CSMA is not justified.

---
# Detailed Real-Time Scenarios: Slotted ALOHA
Slotted ALOHA is the preferred choice for systems that experience higher traffic loads and have the infrastructure to support timing synchronization.

# RFID Tag Communication Systems
RFID is widely used in retail and logistics for inventory tracking.
•	Implementation: When an RFID reader scans a pallet of goods, it uses Slotted ALOHA to prevent hundreds of tags from responding at the exact same time.
•	Why it's used: The reader acts as the "master clock," dictating discrete time slots. Tags are programmed to only respond during these specific slots. This controlled environment significantly reduces the collision rate, allowing the reader to identify multiple items rapidly.
<img width="595" height="381" alt="image" src="https://github.com/user-attachments/assets/40cb882f-252b-4ec1-8fc8-d66b1b5dc307" />

---
# Satellite Data Transmission (VSAT)
VSAT (Very Small Aperture Terminal) networks connect remote locations to a central hub via satellite.
•	Implementation: Used for sending small, intermittent packets of data from terminal stations back to the hub.
•	Why it's used: Because VSAT terminals can receive a timing signal from the central hub, they can synchronize their transmissions into slots. This higher reliability is necessary for commercial data links where Pure ALOHA’s 18.4% efficiency would be too restrictive.
4.3 Cellular Network Call Setup
Before a mobile phone establishes a dedicated high-speed data connection, it must first "introduce" itself to the base station.
•	Implementation: The initial connection request (Random Access Channel) uses Slotted ALOHA.
•	Why it's used: Mobile networks must manage thousands of phones. By forcing request packets into slots synchronized by the base station's pilot signal, the network can handle a much higher volume of simultaneous connection attempts than Pure ALOHA would allow.

# IoT Data Collection (Smart Meters)
While some IoT uses Pure ALOHA for simplicity, others—like smart utility meters—require higher reliability.
•	Implementation: Smart meters for water or electricity send periodic usage data.
•	Why it's used: In high-density urban areas with thousands of meters, Pure ALOHA would lead to constant collisions. By synchronizing meters to discrete time slots, utility companies ensure a more reliable data collection process.
<img width="585" height="384" alt="image" src="https://github.com/user-attachments/assets/517175a4-0a6d-4b24-9a02-c67f301e44f4" />

---
# Cable TV Networks (DOCSIS)
Cable modems use a system similar to VSAT for their "upstream" (user to provider) requests.
•	Implementation: Modems use Slotted ALOHA to send bandwidth requests to the head-end.
•	Why it's used: It provides an efficient way to manage multiple users requesting internet bandwidth simultaneously without the complexity of a fully dedicated line for every user at all times.
Technical Report: Real-Time Scenarios of Pure and Slotted ALOHA Protocols

# Collision Resolution: The Backoff Mechanism
In both real-time scenarios, collisions are inevitable. To ensure the network does not become permanently congested, both protocols utilize a Random Backoff strategy. When a collision occurs, nodes do not retransmit immediately. Instead, they wait for a random duration. This ensures that the two colliding devices do not simply collide again on their second attempt.
# Conclusion
The choice between Pure and Slotted ALOHA is governed by the specific requirements of the real-time scenario. Pure ALOHA remains the king of simplicity and power efficiency, making it the perfect choice for the burgeoning world of uncoordinated IoT devices. Conversely, Slotted ALOHA provides the necessary structure and doubled efficiency required for higher-density commercial applications like cellular networks and RFID systems. Both protocols demonstrate that even "random" access requires a calculated strategy to ensure successful global communication.

# Question Bank - ALOHA Protocols
PART A - Fill in the Blanks
1.	Pure ALOHA has a maximum efficiency of _________%.
2.	In _________ ALOHA, data can only be transmitted at the beginning of a time slot.
3.	LoRaWAN typically uses _________ ALOHA for uplink communication to save energy.
4.	The maximum efficiency of Slotted ALOHA is _________%.
5.	Both protocols require nodes to wait for a _________ amount of time to retransmit after a collision.



PART B - Match the Following
Column A	Column B
1. RFID Systems	a. Uncoordinated / Random timing
2. Pure ALOHA	b. Historically used for Hawaiian satellite links
3. LoRaWAN	c. Uses Slotted ALOHA for multiple tags
4. VSAT	d. Low-power IoT uplink
5. Original ALOHAnet	e. Satellite data transmission using slots
Answer Key: 1-c, 2-a, 3-d, 4-e, 5-b
PART C - True or False
1.	Pure ALOHA is more efficient than Slotted ALOHA. (False)
2.	Cellular networks use Slotted ALOHA for the initial call setup request. (True)
3.	Slotted ALOHA requires all devices to be synchronized to a global clock or beacon. (True)
4.	Collisions cannot occur in Slotted ALOHA. (False)
5.	Pure ALOHA is best suited for high-traffic environments. (False)
PART D - Multiple Choice Questions (MCQs)
1.What is the main advantage of Pure ALOHA?
a. High Efficiency
b. Simplicity and Low Power
c. No Collisions
d. High Speed
Answer: b
2.Which protocol is used by RFID readers to manage multiple tags?
a. Pure ALOHA
b. Slotted ALOHA
c. Token Ring
d. Star Topology
Answer: b
3.What happens in Pure ALOHA if two frames overlap by even a small amount?
a. One frame is saved
b. Both frames are successful
c. A collision occurs and both are lost
d. The frames are merged
Answer: c
4.Which real-time application uses Slotted ALOHA for upstream requests?
a. LoRaWAN
b. Emergency Radio
c. Cable TV Networks (DOCSIS)
d. Simple LANs
Answer: c
PART E - Short Answer Questions
1.	Define the "vulnerable period" in the context of Pure ALOHA.
2.	Why is Slotted ALOHA more efficient than Pure ALOHA?
3.	Explain why LoRaWAN devices prefer Pure ALOHA over Slotted ALOHA.
4.	What is the role of a "Random Backoff" timer?
PART F - Long Answer Questions
1.	Compare Pure ALOHA and Slotted ALOHA with respect to synchronization, efficiency, and real-time use cases.
2.	Elaborate on the real-time implementation of Slotted ALOHA in Cellular Network call setups and RFID systems.
3.	Discuss the limitations of Pure ALOHA and how Slotted ALOHA addresses these issues through timing constraints.





