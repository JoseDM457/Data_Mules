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

---

## 🛠️ Componentes Principales

| Componente | Modelo / Referencia | Cantidad | Función |
| :--- | :--- | :---: | :--- |
| **Microcontrolador** | *[ej. ESP32 / STM32WL]* | 1 | Procesamiento y gestión de energía |
| **Módulo LoRa** | *[ej. SX1276 / RFM95W]* | 1 | Comunicación por radiofrecuencia |
| **Sensor Ambiental** | *[ej. BME280 / SEN55]* | 1 | Lectura de temperatura, humedad y gases |
| **Gestor de Carga** | *[ej. TP4056]* | 1 | Control de batería LiPo |
| **Batería** | *[ej. LiPo 18650 3.7V]* | 1 | Alimentación del nodo |

---

## 📌 Asignación de Pines (Pinout)

### Conexión de Sensores y Módulos

| Módulo / Sensor | Pin del Módulo | Pin del Microcontrolador | Protocolo / Función |
| :--- | :--- | :--- | :--- |
| **Sensor Ambiental** | VCC | 3.3V | Alimentación |
| | GND | GND | Tierra |
| | SDA | GPIO 21 | I2C Data |
| | SCL | GPIO 22 | I2C Clock |
| **Módulo LoRa** | VCC | 3.3V | Alimentación |
| | GND | GND | Tierra |
| | MISO | GPIO 19 | SPI MISO |
| | MOSI | GPIO 23 | SPI MOSI |
| | SCK | GPIO 18 | SPI Clock |
| | CS / NSS | GPIO 5 | Chip Select |
| | DIO0 | GPIO 2 | Interrupción |

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
