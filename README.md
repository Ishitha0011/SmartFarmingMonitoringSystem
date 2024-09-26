# Smart Agriculture Monitoring System IoT

## Project Overview

This project implements a **Smart Agriculture Monitoring System** using **IoT technology**. The system monitors various agricultural parameters such as soil moisture, temperature, humidity, and potential movement in the field. It also provides remote access and control through **Blynk** and **ThingSpeak** for real-time data visualization and analysis. 

This system helps optimize farming practices by providing crucial data to the user via mobile applications and cloud platforms.

## Key Features

- **Real-Time Monitoring**: Sensors continuously monitor temperature, soil moisture, and movements in the field.
- **ThingSpeak Integration**: Data is uploaded to ThingSpeak for cloud-based data storage and real-time monitoring.
- **Blynk Remote Control**: Provides remote monitoring and control via the Blynk app.
- **PIR Motion Detection**: Detects the presence of intruders (such as animals) and triggers an alert system.
- **Relay Control**: Automated relay control for irrigation or other systems based on sensor readings.

## Components

- **ESP8266 WiFi Module**: For internet connectivity.
- **ThingSpeak API**: Cloud-based storage and data visualization.
- **Blynk**: Mobile app for IoT-based remote control.
- **PIR Sensor**: For motion detection.
- **Temperature and Humidity Sensor**: Measures environmental factors.
- **Relay Module**: Controls irrigation or other devices.
  
## How It Works

1. **WiFi Connection**:
   The system connects to WiFi using an ESP8266 module to send sensor data to ThingSpeak and control the system remotely through Blynk.
   
2. **Data Transmission**:
   Sensor readings like soil moisture and temperature are uploaded to the **ThingSpeak** platform using API calls for real-time monitoring.
   
3. **Remote Control**:
   The **Blynk** mobile app allows the user to control the irrigation system and receive notifications if any unusual activity is detected.

4. **Motion Detection**:
   The **PIR sensor** monitors the field for movement and alerts the system if any motion is detected, which can help prevent damage from animals or unauthorized access.

## Code Example

Here is a snippet showing how data is sent to **ThingSpeak** from the system:

```cpp
String thingSpeakAddress = "http://api.thingspeak.com/update?";
String writeAPIKey = "YOUR_API_KEY"; // Enter your ThingSpeak API Key

// Example code to send data to ThingSpeak
WiFiClient client;
String request_string = thingSpeakAddress + "api_key=" + writeAPIKey + "&field1=" + String(temperature) + "&field2=" + String(soilMoisture);

if (client.connect(server, 80)) {
  client.print("GET " + request_string + " HTTP/1.1\r\n" +
               "Host: " + server + "\r\n" +
               "Connection: close\r\n\r\n");
  client.stop();
}
```

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/smart-agriculture-monitoring.git
   cd smart-agriculture-monitoring
   ```

2. **Libraries to Install**:
   - **ESP8266WiFi.h**: For WiFi connectivity.
   - **Blynk.h**: For integrating Blynk for remote monitoring.
   - **ThingSpeak.h**: For sending data to ThingSpeak.

   You can install these libraries via the Arduino Library Manager or by adding them manually.

3. **Upload the code to your ESP8266 board** using the Arduino IDE.

## Circuit Diagram

- **ESP8266 Pinouts**:
   - PIR sensor: Connected to D7.
   - Temperature sensor: Connected to D0.
   - Relay: Connected to D1.

## Future Enhancements

- Add more sensors for monitoring additional parameters like pH levels and nutrient content.
- Implement machine learning algorithms to predict optimal irrigation schedules based on past data trends.
- Introduce SMS alerts for motion detection and environmental changes.
