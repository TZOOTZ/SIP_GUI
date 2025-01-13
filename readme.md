# SIPTester GUI

Generador de tráfico SIP con interfaz gráfica. Permite:
- **Crear y monitorear llamadas SIP** (usando TCP).
- **Enviar `OPTIONS`** periódicos para mantener vivo el trunk o comprobar disponibilidad.
- **Transmitir audio** real (a partir de un MP3) vía RTP para pruebas end-to-end.

## Características

- **Invocación de llamadas**  
  INVITE -> 100 Trying / 180 Ringing -> 200 OK -> ACK. Define cuántas llamadas enviar y a qué ritmo (calls/s).

- **Inyección de audio**  
  Decodifica MP3 a PCM y lo transforma a G.711/Opus (u otro códec SIP) para envío vía RTP.

- **Keep-alive con `OPTIONS`**  
  Envío periódico para checar que el trunk esté “vivo” (UP, DOWN).

- **Interfaz gráfica**  
  Muestra:  
  - Estado de trunk (respuestas `OPTIONS`).  
  - Número de llamadas activas/fallidas.  
  - Tiempo de llamada, codecs y detalles de señalización.

- **Logs y estadísticas**  
  Logs en tiempo real de las transacciones SIP, estadísticas de conectividad, etc.

## Requisitos

- **Sistema Operativo**: Linux (Ubuntu/Debian/CentOS) recomendado.  
- **Node.js** >= 14 (o el stack que prefieras).  
- **Librerías**:  
  - Stack SIP/RTP (PJSIP, ReSIProcate u otro).  
  - Soporte para decodificación MP3 (FFmpeg, libmp3lame, etc.).  
- **(Opcional)** Docker para contenedores.

## Instalación y Ejecución

1. **Clona este repositorio**  
   ```bash
   git clone https://github.com/usuario/SIPTester-GUI.git
   cd SIPTester-GUI

