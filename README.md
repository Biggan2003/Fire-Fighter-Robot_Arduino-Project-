# Fire-Fighter-Robot_Arduino-Project-

<img width="587" height="465" alt="image" src="https://github.com/user-attachments/assets/9f6f3465-9a1a-4b87-8840-0a6da3675b9e" />

# Fire Fighting & Obstacle Avoiding Robot

An autonomous, Arduino-based Fire Fighting Robot designed to detect fire using Flame/IR sensors, navigate towards the location, and automatically extinguish the flame using a mini water pump mechanism mounted on a servo motor.

## 🚀 Features
* **Automated Fire Extinguishing System:** Rotates a mini water pump using a servo motor to spray water precisely at the flame source.
* **Smart Navigation:** Detects the direction of the fire (Left, Front, Right) and moves towards it automatically.
* **Dual-Mode Logic:** Performs close-range firefighting while prioritizing obstacle avoidance and route adjustments during mid-range detection.

---

## 🛠️ Components List
* **Microcontroller:** Arduino Uno (or Arduino Nano)
* **Motor Driver:** L298N Motor Driver Module
* **Chassis Motors:** 4x Yellow DC Gear Motors
* **Actuators:** MG90S Micro Servo Motor & Mini Water Pump (DC 3V-6V)
* **Sensors:** 3x Flame / IR Sensor Modules (Right, Front, Left)
* **Power & Control:** TIP122 Darlington Transistor, 1N4007 Diode, Ceramic Capacitor, SPST Rocker Switch, and 2x 18650 Li-ion Batteries with Holder.

---

## 🔌 Circuit Connection Guide

### Step 1: Main Controller & Power Source
1. Connect the **Positive (+)** wire of the 18650 battery pack to one terminal of the **SPST Switch**.
2. Connect the other terminal of the switch to the **VIN** pin of the Arduino.
3. Connect the **Negative (-)** black wire of the battery directly to the Arduino **GND** pin.

### Step 2: Motor Driver & DC Motors
1. **Power Input:** Connect the battery positive (after the switch) to the **12V** terminal of the L298N module. Connect the L298N **GND** to the Arduino **GND** (Common Ground). Connect the L298N **5V** terminal to the Arduino **5V** pin to power the logic.
2. **Motor Outputs:** Pair the two right motors together and connect them to **OUT1** & **OUT2**. Pair the two left motors together and connect them to **OUT3** & **OUT4**.
3. **Control Signals:** Wire the L298N input pins to the Arduino digital pins as defined below:
   * `enA` ➡️ Arduino Pin **10**
   * `in1` ➡️ Arduino Pin **9**
   * `in2` ➡️ Arduino Pin **8**
   * `in3` ➡️ Arduino Pin **7**
   * `in4` ➡️ Arduino Pin **6**
   * `enB` ➡️ Arduino Pin **5**

### Step 3: Sensors & Actuators
1. **Flame Sensors:** Connect the VCC and GND of all 3 sensors to Arduino 5V and GND. Connect the analog output pins:
   * Right Sensor (`ir_R`) ➡️ Arduino Pin **A0**
   * Front Sensor (`ir_F`) ➡️ Arduino Pin **A1**
   * Left Sensor (`ir_L`) ➡️ Arduino Pin **A2**
2. **Servo Motor:** Connect VCC to 5V, GND to GND, and Signal to Arduino Pin **A4**.
3. **Water Pump (via TIP122):** Connect Arduino Pin **A5** to the Base of the TIP122 transistor through a resistor. Connect the pump through the collector loop with a flyback diode (1N4007) across the pump terminals to prevent back-EMF spikes.

---

## 💻 Firmware Installation Instructions

Follow these steps to upload the source code to your board using the Arduino IDE:

### Step 1: Copy and Paste the Code
1. Open the **Arduino IDE** software on your computer.
2. Clear any default code template so that the sketch page is completely empty.
3. Copy the provided error-free source code and paste it directly into the editor.

### Step 2: Connect your Board
1. Use a compatible USB cable to connect your **Arduino Board** (Uno/Nano) to your computer.
2. The onboard power LED (Red or Blue) should light up immediately, indicating it is receiving power.

### Step 3: Configure Board and Processor Settings
*Go to the top menu bar and select **Tools** to configure your target hardware setup:*
1. **Board:** Navigate to `Tools` ➔ `Board` ➔ `Arduino AVR Boards` ➔ Select **Arduino Nano** (or **Arduino Uno** depending on your board).
2. **Processor:** Navigate to `Tools` ➔ `Processor` ➔ Choose either **ATmega328P** or **ATmega328P (Old Bootloader)** based on your specific chip variant.
3. **Port:** Navigate to `Tools` ➔ `Port` ➔ Select the active **COM Port** assigned to your connected device.

### Step 4: Upload the Code
1. Click the **Upload** button (the right-facing arrow icon `➔`) located in the top-left corner of the interface.
2. The status bar at the bottom will display `Compiling sketch...` followed by `Uploading...`.
3. Once successful, the message will change to **"Done uploading"**, indicating your firmware is active on the board.

> 💡 **Pro-Tip:** While uploading the firmware, it is perfectly safe to leave the sensors and driver signal pins connected. However, always ensure that the main battery power switch for the DC motors and water pump is turned **OFF**. The board safely draws enough power purely from the USB line during programming.

---

## 📄 License
This project is open-source and available under the MIT License.
