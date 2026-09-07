# 🖥️ GALAXY 046 — Estación Terrena

Aplicación web local para la recepción, visualización, graficación y registro de la telemetría de GALAXY 046.

## Flujo de funcionamiento

1. La estación **RX** recibe los datos vía LoRa.
2. RX entrega esos datos mediante conexión **serial** (USB).
3. La **computadora** recibe los datos por el puerto serial.
4. La **aplicación web local** (esta carpeta) interpreta la telemetría recibida.
5. Se **muestran los valores** en tiempo real (T, H, P, Altitud, RSSI, SNR, secuencia).
6. Se **generan gráficos** de la evolución de las variables.
7. Se **visualiza el estado del enlace** (conectado / sin señal, paquetes perdidos).
8. Se pueden **registrar los paquetes** recibidos (log en pantalla / exportación).

## Contenido

```
ground-station/
└── web/
    ├── index.html   → estructura de la interfaz
    ├── style.css    → estilos visuales del dashboard
    └── app.js        → lógica: conexión serial (Web Serial API), parseo y graficado
```

## Cómo usarla

1. Abrir `web/index.html` en un navegador compatible con **Web Serial API** (Chrome / Edge).
2. Conectar la placa RX por USB.
3. Presionar **"Conectar puerto serial"** y seleccionar el puerto correspondiente.
4. La telemetría enviada por RX (una línea JSON por paquete) se mostrará automáticamente en el dashboard.

> ⚠️ Requiere que RX envíe cada paquete por Serial como una línea de texto en formato JSON (ver ejemplo de estructura en el [README principal](../README.md#-telemetría)).

## Estado

Se incluye una versión inicial funcional del dashboard (conexión Web Serial + tabla de valores + gráficos + registro de paquetes). Está preparada para ajustarse al formato exacto del paquete una vez que el firmware definitivo de TX/RX esté listo.
