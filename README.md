# Smart RGB LED Lamp — BLE Controlled (ESP32)

A Bluetooth Low Energy (BLE) controlled RGB LED lamp built on the ESP32 microcontroller.
The lamp supports multiple lighting modes, real-time color and brightness control,
and temperature monitoring — all controllable wirelessly via **nRF Connect** app.
A dedicated mobile application is currently under development.

---

## PCB Design (Eagle)

> Schematic and board layout designed in Eagle CAD.
<p align="center">
<img src="https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/RGBLampSchematic.png" alt="Eagle Schematic" width="500">
</p>
<p align="center">
<img src="https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/RGBLampBoard.png" alt="Eagle PCB Layout" width="500">
</p>
---

## Printed & Assembled PCB

> Physical PCB after printing and soldering.
<p align="center">
<img src="https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/BoardSoldered.jpg" alt="Soldered PCB" width="200" hspace="50"> <img src="https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/EmptyBoard.jpg" alt="Printed PCB" width="200" hspace="10">
</p>
---

## Control via nRF Connect

> The lamp is currently controlled using the **nRF Connect** mobile app.
> Temperature readings are exposed as a BLE characteristic and visible directly in the app.
<p align="center">
<img src="https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/Notify.jpg" alt="nRF Connect - Temperature Reading" width="200">
</p>
---

##  Lighting Modes

### Random Color — Physical Button
> Press the physical button to apply a random color using ESP32's hardware RNG.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d0e5335c-f05f-49c5-abbe-86fba21ef49e" alt="Random Color Button Demo" width="300">
</p>

---

### Candle Mode
> Simulates a realistic flickering candle effect.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6ac1b2ec-f5e1-466f-b5b7-0fba0345dcab" alt="Candle Mode Demo" width="300">
</p>

---

### Pulse Mode
> Smooth brightness breathing effect.

<p align="center">
  <img src="https://github.com/user-attachments/assets/5fb39220-2c33-4e68-8de9-4cd76b4c2ff5" alt="Pulse Mode Demo" width="300">
</p>

---

### Wave Mode
> Seamless smooth transitions across the full RGB spectrum.

<p align="center">
  <img src="https://github.com/user-attachments/assets/83c15daa-1971-4541-ba8f-95a60c9430e5" alt="Wave Mode Demo" width="300">
</p>

---

##  Features

-  **Full RGB color control** — set any color via BLE (values 0–255 per channel)
-  **Brightness control** via MOSFET PWM (low-side configuration)
-  **Temperature monitoring** — DS18B20 sensor exposed as a BLE characteristic
-  **Random color button** — applies a random color using ESP32's hardware RNG
-  **Lighting modes:**
  - Candle (flicker simulation)
  - Pulse (breathing effect)
  - Wave (smooth RGB transitions)
-  **BLE communication** — controlled via nRF Connect (dedicated app in development)

---

##  Pin Configuration (ESP32 DevKit)

| Pin | Function | Component |
|-----|----------|-----------|
| 23 | Red channel (PWM) | RGB LED — Red |
| 24 | Green channel (PWM) | RGB LED — Green |
| 25 | Blue channel (PWM) | RGB LED — Blue |
| 9 | 1-Wire data | DS18B20 Temperature Sensor |
| 11 | Button input | Random color trigger |

---

##  Hardware Components

| Component | Description |
|-----------|-------------|
| **ESP32 DevKit** | Main microcontroller with built-in BLE |
| **RGB LED 3W (Star)** | High-brightness point light source |
| **MOSFET (×3)** | Low-side PWM drivers for each RGB channel |
| **LM2596 Buck Converter Module** | Steps down 12V supply to 3.3V for ESP32 |
| **DS18B20** | Digital 1-Wire temperature sensor |
| **Resistor 33Ω 5W** | Custom current-limiting resistor |
| **Push Button** | Physical control for random color |

>  The repository includes pre-built external libraries for ESP32 DevKit, DS18B20,
> and the custom 33Ω 5W resistor component (Eagle library).

---

##  Libraries

The project uses the following external libraries bundled in the repository:

- `ESP32 BLE Arduino` — BLE GATT server implementation
- `DallasTemperature` + `OneWire` — DS18B20 sensor support
- Custom Eagle component library — 33Ω 5W resistor footprint

---

## Setup

1. Open the project in **Arduino IDE** or **PlatformIO**
2. Select board: `ESP32 Dev Module`
3. Install libraries from the `/libraries` folder (or use the bundled ones)
4. Flash the firmware to your ESP32
5. Open **nRF Connect** on your mobile device
6. Scan for the device and connect
7. Use GATT characteristics to:
   - Write RGB values (3 bytes: R, G, B)
   - Write lighting mode
   - Read temperature

---

##  BLE Control (nRF Connect)

Until the dedicated app is released, the lamp can be fully controlled via **nRF Connect**:

- Write `[R, G, B]` bytes to the color characteristic to set color
- Write a mode byte to switch lighting modes:
  - `Candle` — Candle
  - `Pulse` — Pulse
  - `Wave` — Wave
- Read the temperature characteristic to monitor the LED temperature

---

##  Project Info

- **University:** Silesian University of Technology
- **Faculty:** Faculty of Automatic Control, Electronics and Computer Science
- **Subject:** Microprocessor and embedded systems
- **Author:** Maciej Porębski
