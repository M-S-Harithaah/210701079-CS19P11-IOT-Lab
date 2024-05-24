Urban street lighting is necessary for accessibility and safety, but the present systems sometimes waste energy and need expensive maintenance. Our project uses Internet of Things (IoT) technologies to create 
a Smart Street Light System to try to address these issues. This system uses real-time usage patterns to automatically alter brightness, saving energy during moments of inactivity and improving visibility when 
needed. Proactive problem identification processes also cut maintenance expenses and downtime. Our technology strives to build smarter, more sustainable urban settings through minimizing breakdowns, enhancing 
lighting executives, and lowering energy use.

HARDWARE SPECIFICATIONS FOR APPLICATION
  Processor : Pentium IV Or Higher
  Memory Size : 256 GB (Minimum)
  HDD : 40 GB (Minimum)
SOFTWARE SPECIFICATIONS
  Operating System : WINDOWS 10
  Application : ARDUINO IDE
HARDWARE COMPONENTS FOR PROTOTYPE
  Sensor : IR-Sensor
  Board : Arduino Uno
  Screen : LDR



  CODE EXPLAINATION

  SETUP:
1.Serial.begin(115200): Initializes serial communication at a baud rate of 115200 bits per second. This allows the Arduino to communicate with an external device, such as a computer, over a serial connection.

2.delay(10): Adds a small delay of 10 milliseconds. This delay is often used to allow time for serial communication to initialize properly.

3.Serial.println(F("Adafruit MQTT demo")): Prints the message "Adafruit MQTT demo" to the serial monitor. The 'F()' macro is used to store the string in flash memory, saving RAM space.

4.WiFi.begin(WLAN_SSID, WLAN_PASS): Initiates the connection to the WiFi access point using the SSID (network name) and password provided as constants or variables. It attempts to connect to the WiFi network using the credentials specified.

5.while (WiFi.status() != WL_CONNECTED): Enters a loop that continues until the WiFi connection is successfully established. It continuously checks the status of the WiFi connection.

6.delay(500): Adds a delay of 500 milliseconds between attempts to connect to the WiFi network.

7.Serial.println("WiFi connected"): Prints "WiFi connected" to the serial monitor once the connection is established.

8.Serial.println("IP address: ") Serial.println(WiFi.localIP()): Prints the IP address assigned to the Arduino by the local network. This allows the user to know the IP address of the device, which can be useful for network communication.

9.pinMode(ldr1,INPUT_PULLUP); pinMode(ldr2,INPUT_PULLUP); pinMode(ir1,INPUT_PULLUP); pinMode(ir2,INPUT_PULLUP): Configures the specified pins as inputs with internal pull-up resistors enabled. These pins are likely connected to LDR (Light Dependent Resistor) and IR (Infrared) sensors, which are used to detect ambient light levels and motion, respectively.

LOOP:

1.void loop(): This function is the main execution loop of the Arduino sketch and runs repeatedly after the setup() function.

2.MQTT_connect(): This function is called within the loop to establish a connection to the MQTT broker. If the connection is already established, the function returns without doing anything.

3.if(!digitalRead(ldr1)): Checks the state of the LDR sensor connected to pin ldr1. If the sensor detects low light (indicating darkness), it publishes a message "street light at ambattur working" to the MQTT topic photocell1. Otherwise, it publishes a message "street light at ambattur not working".

4.delay(5000): Adds a delay of 5 seconds after publishing the message to the MQTT topic.

5.if(!digitalRead(ldr2)): Similar to the previous condition, this checks the state of the LDR sensor connected to pin ldr2 and publishes corresponding messages to the MQTT topic photocell2.

6.if(!digitalRead(ir1)): Checks the state of the IR sensor connected to pin ir1. If the sensor detects motion, it sets the LED connected to pin led1 to full brightness (255). Otherwise, it sets the LED brightness to a lower value (50).

7.if(!digitalRead(ir2)): Similar to the previous condition, this checks the state of the IR sensor connected to pin ir2 and controls the LED connected to pin led2 accordingly.

8.void MQTT_connect(): This function handles the MQTT connection process. It attempts to connect to the MQTT broker and retries up to three times if unsuccessful. If the connection is successful, it prints "MQTT Connected!" to the serial monitor.
