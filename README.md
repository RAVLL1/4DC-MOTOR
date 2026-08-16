# 4-Wheel DC Motor Control (Arduino & L293D) 🚗

This project is a practical application of embedded systems and robotics, demonstrating how to control a 4-wheel drive (4WD) chassis using an **Arduino Uno** and an **L293D Motor Driver IC**. The project executes a specific, pre-programmed, time-based movement sequence before automatically shutting down.

## 🧠 Circuit Design & Simulation

Before running the code on physical hardware, the circuit was designed and simulated to ensure proper logic and power distribution:

1. Added an **Arduino Uno**, a **Breadboard**, and an **L293D Motor Driver** IC.
2. Placed four **DC Motors** representing the four wheels of a robot. The motors on the left side are wired in parallel, and the motors on the right side are wired in parallel, allowing them to be controlled as two distinct sets (Left and Right).
3. Connected an external **9V Battery** to the L293D's motor power pin (Pin 8) to ensure the motors receive enough current, keeping the Arduino's logic power separate.
4. Attached the L293D input pins to Arduino digital pins **10 & 9 (Left Motors)** and **6 & 5 (Right Motors)**.
5. Implemented the C++ code to execute a sequence using basic `digitalWrite` logic combined with delays.

<img width="100%" alt="L293D Motor Circuit Simulation" src="image_e4b51c.png" />

---

## 📁 Repository Structure
* `motor_sequence.ino`: The main Arduino C++ sketch containing the movement logic and pin definitions.
* `image_e4b51c.png`: The visual schematic showing the wiring connections between the Arduino, L293D, battery, and motors.

## 🛠 Prerequisites
To build and run this project, you will need the following:

**Hardware:**
* 1x Arduino Uno
* 1x L293D Motor Driver IC (or motor shield)
* 4x DC Gear Motors
* 1x 9V Battery (or appropriate external power supply)
* 1x Breadboard & Jumper Wires

**Software:**
* [Arduino IDE](https://www.arduino.cc/en/software) installed on your computer (or Tinkercad for simulation).

## 🚀 How to Run
1. Wire up the components exactly as shown in the schematic image provided. Ensure grounds are shared between the Arduino and the external battery.
2. Connect your Arduino Uno to your computer using a USB cable.
3. Open the **Arduino IDE** and create a new sketch.
4. Copy the provided C++ code and paste it into the IDE.
5. Go to **Tools > Board** and select **Arduino Uno**.
6. Go to **Tools > Port** and select the port your Arduino is connected to.
7. Click the **Upload** button to compile and flash the code.

## 📊 Expected Behavior (Results)
The code utilizes a `static bool isTaskCompleted` flag to ensure the sequence runs **exactly once** upon startup or reset. The robot will perform the following actions:

1. **Move Forward:** Both left and right motors spin forward for **30 seconds**.
2. **Move Backward:** Both left and right motors reverse for **60 seconds**.
3. **Maneuver Loop (Executes 2 times):**
   * **Turn Right:** Left motors go forward, right motors go backward for **15 seconds**.
   * **Turn Left:** Left motors go backward, right motors go forward for **15 seconds**.
4. **Stop:** All motors power down completely, and the system waits indefinitely.
