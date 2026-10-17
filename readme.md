# Water Bottle Detection Using Raspberry Pi 5 and Ultrasonic Sensor

## Project Overview

This project uses a Raspberry Pi 5, Pi Camera, and ultrasonic sensor to detect the location of a water bottle and execute motion logic based on the model's predictions.

## Hardware Requirements

- Raspberry Pi 5
- Raspberry Pi Camera (PiCam)
- 3.3–5V HC-SR04 Ultrasonic Distance Sensor
- 12V/24V → 6V 10A 60W DC-DC Step-Down Converter
- 5V Buck Converter
- ADATA 64GB A2/U3/V30 MicroSD Card
- Cytron MDD10A Dual-Channel Motor Driver
- Pololu Multi-Hub Wheel w/Inserts for 3mm and 4mm Shafts - 80×10mm
- FIT0522 6V 100 RPM Motor  (3 pack)
- ML5-12 12V 5Ah Battery
- Caster Wheel Package (qty=4)
- Jumper Wires
- Custom OnShape Chassis: https://cad.onshape.com/documents/b67acd9fa4e773602ae2a329/w/8f72ac6179df8e27f44d4304/e/3dcb32b9252e35371910654f?renderMode=0&uiState=6ad39541a3517403a6f1ee55

## GPIO Connections (Raspberry Pi)

| Motor1_In1                     | 11 | GPIO 17 | GPIO.OUT (PWM) |
|--------------------------------|----|---------|----------------|
| Motor1_In2                     | 13 | GPIO 27 | GPIO.OUT (PWM) |
| Motor2_In1                     | 16 | GPIO 23 | GPIO.OUT (PWM) |
| Motor2_in2                     | 18 | GPIO 24 | GPIO.OUT (PWM) |
| Motor1_En                      | 22 | GPIO 25 | GPIO.OUT       |
| Motor2_En                      | 29 | GPIO 5  | GPIO.OUT       |
| Motor_VOLT                     | 4  |         | VOLTS          |
| Motor_GND                      | 6  |         | GND            |
| To Ultrasonic Sensor 3.3V      | 1  |         | VOLTS          |
| Trig                           | 32 | GPIO 12 | GPIO.OUT       |
| Echo                           | 36 | GPIO 16 | GPI.IN         |
| From Ultrasonic Sensor  to GND | 30 |         | GND            |


## Instructions

### 1\. Data Collection

Run `data_collection.py` to generate training images and their corresponding ground-truth labels. These images and labels will be used to train the water bottle detection model.

### 2\. Model Training

Run `Training.py` to train the model using the collected images and ground-truth labels. The training process optimizes the model's weights and biases to minimize prediction error.

### 3\. Real-Time Detection and Motion Control

Run `Run_File.py` to activate the Pi Camera, predict the location of the water bottle using the trained model, and execute the corresponding motion logic.

## Running the Program

Run the following Python files sequentially from the project directory:

```
python data_collection.py
python Training.py
python Run_File.py
```

**Important:** Run each script separately and ensure the previous step has completed before proceeding to the next. The required dependencies, hardware connections, and trained model files must be available before running the program.

## Installation

Clone the repository and install the required dependencies using pip:

`pip install -r requirements.txt`

## Final Notes

- Ensure the Pi Camera and ultrasonic sensor are connected and configured correctly.
- Verify the ultrasonic sensor's wiring and voltage levels fall within range of hardware safety requirements.
