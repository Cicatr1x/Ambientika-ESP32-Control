# Ambientika-ESP32-Control

A simple control system for Ambientika ventilation systems that uses the 24V onboard voltage and an ESP32 to control the fan's direction and speed, as well as a simple automatic mode.

## Components

- **ESP32 D1 Mini**: The microcontroller used to control the fan.
- **MP1584EN DC-DC 3A Step-Down Converter**: The largest block in the schematic, used to step down the 24V to 5V for the ESP32.
- **IRLZ44N N-Channel Mosfet**: Used to control the fan's direction and speed.
- **3 x 10kOhm Resistors**: Used in the voltage divider and as a pull-down resistor.
- **Schottky Diode 1N5819**: Prevents damage to the circuit from inductive back currents during direction changes.
- **24V and GND**: Taken from the 3-pin connector of the Ambientika.

## Circuit Description

- **Voltage Regulation**: The 24V from the Ambientika is stepped down to 5V using the MP1584EN DC-DC Step-Down Converter to provide a suitable supply voltage for the ESP32 D1 Mini.
- **Voltage Divider**: Resistors R1 and R9 form a voltage divider that reduces the 24V to 12V. This voltage range (0-12V) is suitable for controlling the signal pin of the Ambientika.
- **Protection**: The Schottky Diode (1N5819) prevents damage to the circuit from inductive back currents during direction changes.
- **Pull-Down Resistor**: Resistor R10 is connected between the gate and source of the MOSFET as a pull-down resistor to ensure a clear signal at the drain.
- **Fan Connection**: The fan is connected directly to 24V and GND, with the signal voltage taken from the junction of the voltage divider.

## Configuration

The `config` folder contains a sample ESPHome configuration YAML file for setting up the ESP32.

## Usage

1. Connect the components as described in the circuit description.
2. Upload the ESPHome configuration to the ESP32.
3. Power the system using the 24V supply from the Ambientika.
4. Control the fan's direction and speed using the ESP32.

## Automatic Mode

The ESP32 can be configured to automatically control the fan based on sensor inputs or predefined conditions.

---

This project provides a simple and effective way to control Ambientika ventilation systems using an ESP32, making it easy to integrate with home automation systems.
