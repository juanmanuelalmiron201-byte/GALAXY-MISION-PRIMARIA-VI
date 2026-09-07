# 🛰️ GALAXY 046

## Sistema de Telemetría LoRa y Estación Terrena

> Desarrollo, integración y ensayos de un sistema de telemetría basado en **ESP32 + LoRa**, compuesto por una estación transmisora (TX), una estación receptora (RX) y una **estación terrena con interfaz web local**.

[![Estado](https://img.shields.io/badge/estado-en%20desarrollo-yellow)]()
[![Plataforma](https://img.shields.io/badge/hardware-Heltec%20ESP32%20LoRa-blue)]()
[![Enlace](https://img.shields.io/badge/enlace-LoRa%20915%20MHz-orange)]()
[![Licencia](https://img.shields.io/badge/licencia-MIT-green)](LICENSE)

---

## 📡 Descripción

**GALAXY 046** integra sensores ambientales, un enlace de radio **LoRa** y una **estación terrena web** para medir, transmitir, recibir, visualizar y registrar telemetría en tiempo real.

```
SENSORES → TX → LoRa 915 MHz → RX → USB/SERIAL → PC → ESTACIÓN TERRENA WEB
```

---

## 🎯 Misión primaria

| Etapa | Descripción |
|-------|-------------|
| **Medir** | Temperatura (T), Presión (P), Altitud (A) y Humedad (H) — con BMP280 y DHT11 |
| **Transmitir** | TX arma el paquete y lo envía por LoRa |
| **Recibir** | RX recibe el paquete y agrega RSSI/SNR |
| **Visualizar** | RX entrega los datos por Serial a la estación terrena web |
| **Graficar** | La web muestra valores, gráficos, estado del enlace y registro de paquetes |

> ⚠️ Los resultados de alcance de este repositorio **no** son el alcance máximo teórico de LoRa: son la mayor distancia **documentada** durante los ensayos (≈ 2,5 km). Ver [`docs/mision.md`](docs/mision.md).

---

## 🌡️ Variables medidas

| Variable | Símbolo | Unidad |
|----------|---------|--------|
| Temperatura | T | °C |
| Humedad | H | %RH |
| Presión | P | hPa |
| Altitud | A | m |
| RSSI | RSSI | dBm |
| SNR | SNR | dB |

---

## 📦 Telemetría — ejemplo de formato

```json
{
  "t": 25.4,
  "h": 62.1,
  "p": 1012.4,
  "alt": 425.3,
  "rssi": -72,
  "snr": 8.5,
  "seq": 154
}
```

> Solo a modo de ejemplo de estructura, los valores no son datos reales.

---

## 📤 Estación TX / 📥 Estación RX

- **TX** — lee **BMP280** (T, P, A) y **DHT11** (H), arma el paquete y transmite por LoRa. Ver [`firmware/TX/`](firmware/TX/).
- **RX** — recibe el paquete, agrega RSSI/SNR y lo reenvía por Serial. Ver [`firmware/RX/`](firmware/RX/).
- Frecuencia utilizada en los ensayos: **915 MHz**. Antenas: las originales de los módulos (≈ 5 cm).

---

## 🖥️ Estación terrena / interfaz web local

**GALAXY 046 — ESTACIÓN TERRENA** — lee el puerto serial (Web Serial API), muestra los valores en tiempo real, genera gráficos, indica el estado del enlace y registra los paquetes recibidos.

Código en [`ground-station/`](ground-station/).

---

## 🧭 Ensayos de campo y resultados

| Ensayo | Ubicación | Distancia aproximada | Resultado |
|--------|-----------|----------------------|-----------|
| 01 | Mirador de Alta Gracia – Camino Autoquemado | 1.250 m | Comunicación registrada |
| 02 | Alta Gracia – estación de servicio | 1.600 m | Comunicación registrada |
| 03 | Camino de los Lecheros – Ruta C45 | 2.500 m | Mayor distancia documentada |

> La distancia máxima **documentada** fue de aproximadamente **2,5 km** (Ensayo 03).

Detalle: [Ensayo 01](docs/ensayo-01.md) · [Ensayo 02](docs/ensayo-02.md) · [Ensayo 03](docs/ensayo-03.md) · [Informe técnico completo](docs/informe-tecnico.md) · [Resultados](docs/resultados.md)

**Posible factor de interferencia:** durante el Ensayo 03 se identificó una infraestructura eléctrica de EPEC a ≈5 m del recorrido. Se menciona únicamente como posible factor, sin confirmación experimental. Otros factores considerados: humedad, lluvia, vegetación húmeda, condiciones atmosféricas, terreno y obstáculos.

---

## 📁 Fotos, videos y mapas — todo en Google Drive

Todo el material multimedia (fotos, videos, mapas de los recorridos) está en Google Drive, no en el repositorio:

| Recurso | Enlace |
|---|---|
| 📁 Evidencia de campo / Fotografías | [Drive 01](https://drive.google.com/drive/folders/1RCjKh5fF5i0fqXdPV03HzA_QGnm-VxcI?usp=sharing) |
| 📁 Material adicional 02 | [Drive 02](https://drive.google.com/drive/folders/1jcrtFJef4QxO1c2YG2vYs9FsQ9KlmG8y?usp=sharing) |
| 📁 Material adicional 03 | [Drive 03](https://drive.google.com/drive/folders/13ETTX8Yo8WBkovQU4PMOZxJaV9mcvktG?usp=sharing) |
| 📁 Material adicional 04 | [Drive 04](https://drive.google.com/drive/folders/1UU41_7nAgjw4GVSEalrkk1nJEZbV5FOn?usp=sharing) |
| 📁 Documentación técnica / Informes | [Documentación técnica](https://drive.google.com/drive/folders/1MfNvUf_le6TLeoVVfSb-Ug_T-c15wVmi?usp=sharing) |

---

## 🗂️ Estructura del repositorio

```
GALAXY-046/
│
├── README.md
├── LICENSE
├── COMO_SUBIR_A_GITHUB.md
│
├── firmware/
│   ├── TX/
│   │   ├── TX.ino        (BMP280 + DHT11 → LoRa)
│   │   └── README.md
│   └── RX/
│       ├── RX.ino
│       └── README.md
│
├── ground-station/
│   ├── web/
│   │   ├── index.html
│   │   ├── style.css
│   │   └── app.js
│   └── README.md
│
├── docs/
│   ├── mision.md
│   ├── ensayo-01.md
│   ├── ensayo-02.md
│   ├── ensayo-03.md
│   ├── informe-tecnico.md
│   └── resultados.md
│
└── data/
    ├── telemetry/
    ├── logs/
    └── README.md
```

---

## 🚀 Trabajo futuro

- Evaluación de antenas externas.
- Ampliación de los ensayos de alcance.
- Incorporación de GPS.
- Registro histórico de telemetría.

---

## ✅ Conclusiones

GALAXY 046 integra una cadena de telemetría completa — **medición → transmisión → recepción → procesamiento → visualización → graficación → registro** — validada con ensayos de campo reales, alcanzando una distancia máxima documentada de ≈2,5 km.

---

<p align="center">
📡 <b>GALAXY 046</b> — Sistema de Telemetría LoRa y Estación Terrena
</p>
