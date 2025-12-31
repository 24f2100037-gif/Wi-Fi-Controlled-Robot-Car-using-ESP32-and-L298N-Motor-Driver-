**Wi-Fi Controlled Robot Car using ESP32 and L298N Motor Driver**                                       		by Harsh Rathee 

**1\. Introduction**  
This project focuses on the development of a Wi-Fi-controlled robot car using an ESP32 microcontroller and an L298N motor driver. The ESP32 acts as the brain of the robot, allowing remote control via a web-based interface. The L298N module manages the DC motors' movement, enabling the car to move forward, backward, left, and right wirelessly.

**2\. Objectives**

* To design and implement a Wi-Fi-controlled robot car using ESP32.  
* To establish a web server on the ESP32, enabling real-time control via a web browser.  
* To integrate DC motors with L298N motor driver, ensuring smooth and efficient movement.  
* To explore the applications of IoT in robotics and automation.

**3\. Components Used**

| Component	 | Purpose |
| :---- | :---- |
| ESP32 microcontroller | Controls the robot wirelessly |
| L298N Motor Driver | Drives DC motors |
| DC Motors | Provides movement |
| Li-ion Batteries (3.7V each) | Power source (connected in series) |

**4\. Methodology**  
Step 1: **ESP32 Setup**

* The ESP32 is programmed using Arduino IDE with the ESP32 board library.  
* Wi-Fi credentials are configured for remote connectivity.

Step 2: **Web Server Implementation**

* The ESP32 hosts a simple web page with buttons for robot control.  
* When a button is clicked, an HTTP request is sent to the ESP32, triggering motor movement.

Step 3: **Motor Driver Configuration**

* The L298N driver is connected to the ESP32 and controls the DC motors via GPIO pins.  
* The motors are enabled using ENA and ENB pins.  
* Movement functions such as forward, backward, left, and right are implemented in code.

Step 4: **Power Management**

* Three Li-ion batteries in series provide \~11.1V for the L298N motor driver.  
* A regulated 3.3V power source supplies the ESP32.

**5\. Code Implementation**  
The ESP32 runs a program that:

1. Connects to Wi-Fi.  
2. Hosts a web server with an interface.  
3. Detects user commands (/forward, /backward, etc.).  
4. Controls the motors based on received commands.

**Key Code Functions:**  
void moveForward() {   
digitalWrite(IN1, HIGH);  
 digitalWrite(IN2, LOW);   
digitalWrite(IN3, HIGH);  
 digitalWrite(IN4, LOW);   
analogWrite(ENA, 255);   
analogWrite(ENB, 255);   
}   
This function sets the appropriate GPIO pins high and low to move the robot forward.

**6\. Results & Observations**

* The ESP32 successfully connects to Wi-Fi and hosts a web server.  
* The web interface loads correctly, displaying control buttons.  
* The forward command works, but initially, only two motors were moving.  
* Debugging helped resolve GPIO pin issues, enabling all four motors to function correctly.  
* A stable power supply is essential to prevent ESP32 resets.

**7\. Challenges & Solutions**  
**Issue**: ESP32 Reset Loop  
**Cause:** Insufficient power or unstable voltage.  
**Solution**: Used a high-power source and verified wiring.

**Issue:** Only Two Motors Moving  
**Cause:** Incorrect wiring or motor driver configuration.  
**Solution:** Rechecked connections, ensured both ENA and ENB were activated, and debugged GPIO outputs.

**Issue:** Wi-Fi Not Connecting  
**Cause**: Incorrect SSID/password or weak signal.  
**Solution**: Verified credentials, restarted the router, and limited connection retries.

**8\. Future Enhancements**

* Speed Control: Adjust motor speed dynamically using PWM signals.  
* Obstacle Avoidance: Integrate ultrasonic sensors for autonomous movement.  
* Voice Control: Implement speech recognition to control the robot using voice commands.  
* Camera Integration: Add a camera module for real-time video streaming.


**9\. Conclusion**  
This project demonstrates wireless control of a robot car using ESP32 and L298N, showcasing the power of IoT and robotics. Through troubleshooting and debugging, the system now operates smoothly. Future upgrades can enhance automation, making the robot more interactive and intelligent.

**10\. Sample Video**  
   
[sample video of robo car](https://www.youtube.com/shorts/vDL7K7nAdws)

