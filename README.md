**Sensor Anomaly Detection System** <br><br>
This project implements an advanced Sensor Anomaly Detection System for real-time monitoring and analysis of sensor data. The system uses a combination of hardware components and software to detect anomalies in sensor data and ensure timely intervention in critical systems. <br><br>

**Features:** <br>
Real-time anomaly detection using sensor data, leveraging both statistical and rule-based methods. <br>
STM32F4VGT6 microcontroller for data acquisition and processing. <br>
FreeRTOS for task scheduling, ensuring responsive and efficient management of multiple concurrent operations.<br>
CAN bus communication for transferring sensor data to the ESP32 WROOM-E.<br>
Cloud communication via MQTT for remote monitoring, analysis, and alerting.<br>
On-site visualization using an SPI Screen Module TFT Interface for displaying sensor data.<br><br>
**Two main anomaly detection techniques:** <br>
Z-score method for statistical anomaly detection.  <br>
Rule-based approach for predefined threshold-based anomaly detection.  <br> <br>
**System Overview** <br>
The sensor anomaly detection system is designed to operate autonomously in real-time while maintaining high reliability and efficiency. Below is a breakdown of its main components and how they interact:  <br>

**Components**  <br>
**STM32F4VGT6 Microcontroller** <br>

The core of the system, this microcontroller is responsible for acquiring data from sensors, processing it, and performing the anomaly detection algorithms.
It runs FreeRTOS for efficient management of multiple tasks, including sensor reading, anomaly detection, and data transmission. <br>
**FreeRTOS**  <br>

FreeRTOS is used to schedule tasks, such as reading sensor data, detecting anomalies, and communicating with the ESP32 module. It ensures that the system remains responsive and can handle real-time sensor data without delays.  <br>
**CAN Bus**  <br>

The Controller Area Network (CAN bus) is used to transmit sensor data from the STM32F4VGT6 microcontroller to the ESP32 WROOM-E module. This bus system is robust and allows for reliable data transmission even in noisy environments. <br>
**ESP32 WROOM-E Module**  <br>

The ESP32 is used for cloud communication. It receives data from the STM32 via CAN bus and sends it to a cloud service using the MQTT protocol. This enables remote monitoring, analysis, and alerting based on detected anomalies. <br>
**SPI Screen Module (TFT Interface)**  <br>

A TFT LCD screen connected via SPI is used to display key sensor metrics locally, enabling real-time decision-making on-site. This visual interface helps users monitor the system without needing to access the cloud.  <br>
**Anomaly Detection**  <br>
Two primary anomaly detection methods are implemented to ensure the system can accurately identify unusual sensor readings:  <br>

*Z-score Method:*  <br>

This statistical method computes the Z-score of incoming sensor data to detect outliers. A high Z-score indicates that the sensor reading is significantly different from the mean, potentially indicating an anomaly.  <br>
*Rule-based Approach:*  <br>

Custom thresholds are defined based on expected sensor behavior. If the sensor data exceeds or falls below these thresholds, an anomaly is flagged. This approach is suitable for detecting known, predefined issues in the system. <br>
Both methods are implemented to complement each other and provide a more comprehensive anomaly detection system. <br><br>

**Installation** <br>
*Prerequisites* <br>
Before getting started, you will need to set up the following tools and environments: <br>

*STM32CubeIDE:*  <br>Used for programming the STM32F4VGT6 microcontroller. <br>

[Download STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html) <br>
*Arduino IDE:*<br> Required for programming the ESP32 WROOM-E module. <br>

[Download Arduino IDE](https://www.arduino.cc/en/software) <br>
*MQTT Broker:* <br> You will need a cloud-based MQTT broker for remote monitoring. <br>

You can use services like HiveMQ, Mosquitto, or set up your own MQTT broker. <br>
Step 1: Clone the Repository <br>
Open bash <br>
Copy <br>
*git clone https://github.com/yourusername/sensor-anomaly-detection.git* <br>
*cd sensor-anomaly-detection* <br> <br>
Step 2: STM32F4 Development Environment Setup <br>
Open STM32CubeIDE. <br>
Open the project folder and configure the STM32F4 microcontroller. <br>
Enable the required peripherals, such as CAN bus, SPI (for TFT), and any other communication interfaces. <br>
Ensure that FreeRTOS is properly configured for multitasking. <br>
Compile and flash the firmware onto the STM32F4VGT6. <br><br>
Step 3: Set Up the ESP32 <br>
Open Arduino IDE. <br>
Go to File > Preferences and add the ESP32 board manager URL. <br>
Install the ESP32 board support. <br>
Open the ESP32 code file, configure the Wi-Fi credentials and MQTT settings (broker URL, topic, etc.). <br>
Upload the code to the ESP32 WROOM-E module. <br><br>
Step 4: Set Up MQTT Broker <br>
If you're using a service like HiveMQ or Mosquitto, follow the setup instructions to create an MQTT broker and obtain the connection details (broker URL, username, password, etc.). <br>
Make sure the ESP32 is configured with these details so it can connect and send sensor data to the cloud. <br>
Step 5: SPI Screen Module Setup <br>
Connect the SPI TFT screen to the STM32F4VGT6 microcontroller. <br>
Update the code to display relevant sensor data on the screen. This may include the current sensor values, anomaly status, and other metrics. <br><br>
**Usage** <br>
Monitoring Anomalies<br>
Once the system is up and running, it will continuously monitor sensor data in real-time. The following steps outline the key operations of the system: <br>

*Local Display:* The SPI TFT screen will show sensor values and anomaly status on-site. If an anomaly is detected, the screen will show a warning or highlight the issue for local attention. <br>

*Cloud Monitoring:* The ESP32 WROOM-E module will periodically send sensor data to the cloud via MQTT. Remote users can connect to the MQTT broker to receive real-time sensor readings and alerts. <br>

*Anomaly Detection:* The system uses the Z-score method and rule-based approach to detect anomalies in sensor data. If an anomaly is detected, the system will flag it locally on the display and remotely in the cloud. <br>

*Alerts:* Optionally, the system can be configured to send email or SMS alerts if an anomaly exceeds a critical threshold. <br><br>

**Example Data Flow**
Sensors generate data. <br>
The STM32F4VGT6 microcontroller collects and processes the data. <br>
FreeRTOS schedules tasks to detect anomalies and send data to the ESP32. <br>
The ESP32 sends the data to the cloud using MQTT. <br>
Data is visualized on the SPI TFT screen and/or remote cloud dashboard. <br><br>
**Contributing**
We welcome contributions to improve the functionality and performance of this project. If you'd like to contribute, please follow these steps: <br>

Fork the repository to your own GitHub account. <br>
Create a new branch for your feature or fix (git checkout -b feature-name). <br>
Make changes and commit them (git commit -am 'Added new feature'). <br>
Push the changes to your fork (git push origin feature-name). <br>
Submit a pull request with a description of your changes. <br>
**License**
This project is licensed under the MIT License - see the LICENSE file for details.
