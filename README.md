# Smart RGB LED Lamp — BLE Controlled (ESP32)

A Bluetooth Low Energy (BLE) controlled RGB LED lamp built on the ESP32 microcontroller.
The lamp supports multiple lighting modes, real-time color and brightness control,
and temperature monitoring — all controllable wirelessly via **nRF Connect** app.
A dedicated mobile application is currently under development.

---

## PCB Design (Eagle)

> Schematic and board layout designed in Eagle CAD.

![Eagle Schematic & PCB Layout](https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/RGBLampSchematic.png)
![alt text](https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/RGBLampBoard.png)
---

## Printed & Assembled PCB

> Physical PCB after printing and soldering.

![Printed PCB](https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/EmptyBoard.jpg)


![Soldered PCB](https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/BoardSoldered.jpg)

---

## Control via nRF Connect

> The lamp is currently controlled using the **nRF Connect** mobile app.
> Temperature readings are exposed as a BLE characteristic and visible directly in the app.

![nRF Connect — Temperature Reading](https://github.com/Paciej/RGB-Lamp/blob/main/hardware/Pictures/Notify.jpg)

---

## Demo Videos

| Mode | Description | Link |
|------|-------------|------|
| 🎲 Random Color Button | Press the physical button to apply a random color (ESP32 hardware RNG) | [▶ Watch](https://github.com/user-attachments/assets/2d8df29d-432d-4193-9d58-128e2afa2573) |
| 🕯️ Candle Mode | Simulates a flickering candle effect | [▶ Watch][https://github.com/user-attachments/assets/b84fc6cb-8e51-45d1-a9a4-e45dd6cf49fe ] |
| 💓 Pulse Mode | Smooth brightness pulsing | [▶ Watch][https://github.com/user-attachments/assets/e08484a1-ccfc-4352-95d7-4a24032cc361] |
| 🌈 Wave Mode | Smooth RGB color transitions | [▶ Watch][https://github.com/user-attachments/assets/66ebcfb8-80b2-4348-9ec0-0ef78081138d ] |

---

## ⚙️ Features

- 🎨 **Full RGB color control** — set any color via BLE (values 0–255 per channel)
- 🔆 **Brightness control** via MOSFET PWM (low-side configuration)
- 🌡️ **Temperature monitoring** — DS18B20 sensor exposed as a BLE characteristic
- 🎲 **Random color button** — applies a random color using ESP32's hardware RNG
- 💡 **Lighting modes:**
  - Static color
  - Candle (flicker simulation)
  - Pulse (breathing effect)
  - Wave (smooth RGB transitions)
- 📶 **BLE communication** — controlled via nRF Connect (dedicated app in development)

---

## 🔌 Pin Configuration (ESP32 DevKit)

| Pin | Function | Component |
|-----|----------|-----------|
| 23 | Red channel (PWM) | RGB LED — Red |
| 24 | Green channel (PWM) | RGB LED — Green |
| 25 | Blue channel (PWM) | RGB LED — Blue |
| 9 | 1-Wire data | DS18B20 Temperature Sensor |
| 11 | Button input | Random color trigger |

---

## 🧩 Hardware Components

| Component | Description |
|-----------|-------------|
| **ESP32 DevKit** | Main microcontroller with built-in BLE |
| **RGB LED 3W (Star)** | High-brightness point light source |
| **MOSFET (×3)** | Low-side PWM drivers for each RGB channel |
| **LM2596 Buck Converter Module** | Steps down 12V supply to 3.3V for ESP32 |
| **DS18B20** | Digital 1-Wire temperature sensor |
| **Resistor 33Ω 5W** | Custom current-limiting resistor |
| **Push Button** | Physical control for random color |

> 📦 The repository includes pre-built external libraries for ESP32 DevKit, DS18B20,
> and the custom 33Ω 5W resistor component (Eagle library).

---

## 📚 Libraries

The project uses the following external libraries bundled in the repository:

- `ESP32 BLE Arduino` — BLE GATT server implementation
- `DallasTemperature` + `OneWire` — DS18B20 sensor support
- Custom Eagle component library — 33Ω 5W resistor footprint

---

## 🚀 Getting Started

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

## 📡 BLE Control (nRF Connect)

Until the dedicated app is released, the lamp can be fully controlled via **nRF Connect**:

- Write `[R, G, B]` bytes to the color characteristic to set color
- Write a mode byte to switch lighting modes:
  - `0x00` — Static
  - `0x01` — Candle
  - `0x02` — Pulse
  - `0x03` — Wave
- Read the temperature characteristic to monitor the LED temperature

---

## 🏫 Project Info

- **University:** Silesian University of Technology
- **Faculty:** Faculty of Automatic Control, Electronics and Computer Science
- **Subject:** SMiW
- **Author:** Maciej Porębski
