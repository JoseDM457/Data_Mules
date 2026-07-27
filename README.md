# Data Mules 🚲🛰️

> Sistema móvil y de bajo consumo para el monitoreo ambiental urbano mediante un modelo de comunicación Store–Carry–Forward sobre LoRaWAN.

---

## 📝 Descripción del Proyecto

**Data Mules** es una plataforma de monitoreo ambiental diseñada para recopilar datos clave en entornos urbanos donde la cobertura de red no es continua. El sistema aprovecha la movilidad de vehículos (nodos móviles) para recolectar, almacenar de forma local y reenviar parámetros ambientales cuando se detecta una puerta de enlace (*gateway*) o un nodo cercano.

---

## ✨ Características Generales

* **Modelo de Comunicación:** Basado en *Store–Carry–Forward* (Almacenamiento, transporte y reenvío).
* **Protocolo Inalámbrico:** Cobertura oportunista mediante LoRaWAN / LoRa P2P.
* **Bajo Consumo:** Optimizado para funcionar de forma autónoma con baterías o energía cosechada.
* **Parámetros Medidos:** Temperatura, humedad y calidad del aire.
* **Almacenamiento Local:** Memoria no volátil integrada para retener mediciones sin conexión.

## 🛠️ Componentes Principales

| Componente | Referencia / Modelo | Cantidad | Función / Descripción |
| :--- | :--- | :---: | :--- |
| **Placa de Control / LoRa** | BastWAN (Headers U2, U3) | 1 | Microcontrolador principal con conectividad LoRa integrada[cite: 1]. |
| **Sensor Ambiental** | BME680 (U4) | 1 | Medición de temperatura, humedad, presión atmosférica y calidad del aire[cite: 1]. |
| **Módulo GPS** | GT-U7 (U11) | 1 | Geolocalización en tiempo real del nodo móvil[cite: 1]. |
| **Pantalla Display** | OLED I2C HS13L03B2C01 (U10) | 1 | Visualización local de estados y mediciones[cite: 1]. |
| **Lector MicroSD** | Molex 1040310811 (SIM1) | 1 | Almacenamiento local de datos (*Store-Carry-Forward*)[cite: 1]. |
| **Cargador de Baterías** | BQ25887RGER (U1) | 1 | Gestor de carga inteligente I2C para arreglo de baterías 2S[cite: 1]. |
| **Regulador de Voltaje** | AMS1117-5.0 (U18) | 1 | Regulador lineal para línea de alimentación de 5V[cite: 1]. |
| **Conector de Baterías** | BH-18650-A6AJ012 (U12, U13) | 2 | Portabaterías para celdas Li-ion 18650 en serie (2S)[cite: 1]. |
| **Sensor de Temp. Externa** | Clemas DB125-3.5-2P (U14, U15) | 2 | Terminales de conexión para sensor de temperatura DS18B20[cite: 1]. |
| **Puerto USB** | USB-C U262-161N-4BVC11 (USB1) | 1 | Interfaz de alimentación y carga de batería[cite: 1]. |

---

## 📌 Asignación de Pines (Pinout)

### Bus de Comunicaciones e Interfaces

| Periférico | Pin del Módulo | Pin BastWAN | Protocolo / Función | Observaciones |
| :--- | :--- | :--- | :--- | :--- |
| **BME680** | SDA | SDA (U2-12) | I2C | Bus I2C principal (Pull-ups R1 y R2 de 4.7kΩ)[cite: 1] |
| | SCL | SCL (U2-11) | I2C | Bus I2C principal[cite: 1] |
| **Pantalla OLED** | SDA | SDA (U2-12) | I2C | Bus I2C principal[cite: 1] |
| | SCL | SCL (U2-11) | I2C | Bus I2C principal[cite: 1] |
| **Cargador BQ25887**| SDA | SDA (U2-12) | I2C | Bus I2C principal[cite: 1] |
| | SCL | SCL (U2-11) | I2C | Bus I2C principal[cite: 1] |
| **Módulo GPS GT-U7**| TXD | RX (U3-14) | UART RX | Recepción de datos NMEA[cite: 1] |
| | RXD | TX (U3-15) | UART TX | Transmisión de comandos[cite: 1] |
| **Lector MicroSD** | SCK (CLK) | SCK (U3-11) | SPI Clock | Reloj de bus SPI[cite: 1] |
| | DAT0 (DO) | MISO (U3-13) | SPI MISO | Entrada de datos SPI[cite: 1] |
| | CMD (DI) | MOSI (U3-12) | SPI MOSI | Salida de datos SPI[cite: 1] |
| | CD/DAT3 (CS) | Pin 10 (U2-7) | SPI CS | Chip Select para MicroSD[cite: 1] |
| **Sensor DS18B20** | DATA | Pin A0 (U3-5) | 1-Wire / GPIO | Lectura digital con Pull-up R11 (4.7kΩ)[cite: 1] |

---

## 🖼️ Imágenes del Diseño

### Esquema y PCB

| Esquema Electrónico | Diseño de PCB |
| :---: | :---: |
| ![Esquema Electrónico](docs/images/schematic.png) | ![PCB Top/Bottom](docs/images/pcb_layout.png) |

### Prototipo Ensamblado

![Prototipo Data Mules](docs/images/prototype.jpg)
*Figura 1: Vista del nodo sensor integrado en el chasis vehicular.*

---

## 🛡️ Certificación OSHW

Este proyecto cumple con la definición de **Hardware de Código Abierto (OSHW)** y está certificado por la *Open Source Hardware Association (OSHWA)*.

* **UID de Certificación OSHWA:** `[ej. ES000001]`
* **Enlace al Registro Oficial:** [Ver Certificación en OSHWA](https://certification.oshwa.org/)

![OSHWA Badge](https://raw.githubusercontent.com/oshwa/oshw-badges/main/osw-certified-mark/svg/OSHW_mark_US000000.svg)

---

## 📜 Licencias

Este proyecto utiliza licencias de código abierto independientes para software y hardware:

* **Hardware:** [CERN-OHL-P-2.0](https://cern-ohl.web.cern.ch/) *(o la licencia de HW que elijas, ej. CC-BY-SA 4.0)*.
* **Software / Firmware:** [MIT License](LICENSE-MIT) *(o GPLv3, Apache 2.0)*.
* **Documentación:** [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).
