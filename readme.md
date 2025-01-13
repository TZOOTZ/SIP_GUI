# SIPTester GUI

Generador de tráfico SIP con interfaz gráfica. Permite:
- **Crear y monitorear llamadas SIP** (usando TCP).
- **Enviar `OPTIONS`** periódicos para mantener vivo el trunk o comprobar disponibilidad.
- **Transmitir audio** real (a partir de un MP3) vía RTP para pruebas end-to-end.

---

## Características

- **Invocación de llamadas**  
  INVITE -> 100 Trying / 180 Ringing -> 200 OK -> ACK.  
  Define cuántas llamadas enviar y a qué ritmo (calls/s).

- **Inyección de audio**  
  Decodifica MP3 a PCM y lo transforma a G.711/Opus (u otro códec SIP) para envío vía RTP.

- **Keep-alive con `OPTIONS`**  
  Envío periódico para checar que el trunk esté “vivo” (UP o DOWN).

- **Interfaz gráfica**  
  Muestra:  
  - Estado de trunk (respuestas `OPTIONS`).  
  - Número de llamadas activas/fallidas.  
  - Tiempo de llamada, codecs y detalles de señalización.

- **Logs y estadísticas**  
  Logs en tiempo real de las transacciones SIP y métricas de conectividad.

---

## Arquitectura y Árbol de Carpetas

```plaintext
project/
├─ server/
│   ├─ src/
│   │   ├─ config/
│   │   │   └─ default.js            // Config general (puertos SIP, logs, etc.)
│   │   ├─ sip/
│   │   │   ├─ sipStack.js           // Manejo SIP (INVITE, OPTIONS, etc.)
│   │   │   ├─ rtpHandler.js         // Manejo RTP (envío/recepción)
│   │   │   └─ audioPlayer.js        // Decodifica MP3 y codifica a códec SIP
│   │   ├─ controllers/
│   │   │   └─ callsController.js     // Lógica de llamadas
│   │   ├─ services/
│   │   │   └─ trunkMonitor.js        // Envío periódico de OPTIONS
│   │   ├─ routes/
│   │   │   └─ index.js              // Endpoints o WebSockets
│   │   ├─ utils/
│   │   │   └─ logger.js             // Manejo de logs
│   │   └─ server.js                 // Punto de arranque
│   ├─ package.json
│   └─ README.md
│
├─ client/
│   ├─ public/
│   │   └─ index.html
│   ├─ src/
│   │   ├─ components/
│   │   │   ├─ CallMonitor.jsx
│   │   │   ├─ TrunkStatus.jsx
│   │   │   └─ ConfigPanel.jsx
│   │   ├─ pages/
│   │   │   └─ Home.jsx
│   │   ├─ services/
│   │   │   └─ api.js
│   │   └─ App.jsx
│   ├─ package.json
│   └─ README.md
│
└─ docker/
    ├─ Dockerfile.server
    ├─ Dockerfile.client
    └─ docker-compose.yml

## Requisitos

- **Sistema Operativo**: Linux (Ubuntu/Debian/CentOS) recomendado.  
- **Node.js** >= 14 (o el stack que prefieras).  
- **Librerías**:  
  - Stack SIP/RTP (PJSIP, ReSIProcate, etc.).  
  - Soporte para decodificación MP3 (FFmpeg, libmp3lame, etc.).  
- **(Opcional)** Docker para contenedores.

---

## Instalación y Ejecución

1. **Clona este repositorio**  
   ```bash
   git clone https://github.com/usuario/SIPTester-GUI.git
   cd SIPTester-GUI


## Uso
Config Panel
Ingresa IP/puerto del servidor SIP, intervalos de OPTIONS, codecs, etc.
Subir archivo de audio
Carga un MP3. La app lo decodifica y prepara para envío vía RTP.
Generar llamadas
Ajusta cuántas llamadas simultáneas o la tasa de generación (calls/s).
Observa en tiempo real el estado de cada llamada (RINGING, CONNECTED, etc.).
Monitoreo
Visualiza la respuesta de OPTIONS (UP, DOWN).
Ve cuántas llamadas están en RINGING, CONNECTED, FAIL, etc.
Logs
Todos los mensajes SIP y estadísticas se almacenan en consola o en archivo, según configuración.

