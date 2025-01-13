# SIPTester GUI TZOOTZ RESEARCH

Una herramienta moderna para pruebas de trunks SIP con interfaz gráfica intuitiva.

## 🚀 Descripción

SIPTester GUI es una aplicación que permite generar, monitorear y administrar llamadas SIP a través de una interfaz gráfica amigable. Diseñada para simplificar las pruebas de rendimiento y calidad en sistemas de telefonía IP.

### Características Principales

- 📞 Generación y gestión de llamadas SIP vía TCP
- 🔄 Monitoreo de trunks mediante OPTIONS periódicos
- 🎵 Inyección de audio personalizado para pruebas end-to-end
- 📊 Estadísticas en tiempo real
- 🎯 Interfaz intuitiva para configuración y monitoreo

## 🛠️ Arquitectura

### Backend (Server)

El servidor está construido con Node.js y se estructura en módulos especializados:

- `sipStack.js`: Control de señalización SIP
- `rtpHandler.js`: Gestión del transporte RTP
- `audioPlayer.js`: Procesamiento y codificación de audio
- `trunkMonitor.js`: Sistema de monitoreo de trunks

### Frontend (Client)

Interfaz desarrollada en React con componentes modulares:

- `TrunkStatus`: Visualización del estado del trunk
- `CallMonitor`: Panel de llamadas activas
- `ConfigPanel`: Configuración del sistema

## ✨ Funcionalidades

### Gestión de Llamadas SIP
- Flujo completo de señalización (INVITE → 100/180 → 200 OK → ACK)
- Control de concurrencia y tasa de llamadas
- Monitoreo en tiempo real

### Manejo de Audio
- Soporte para múltiples formatos (MP3, WAV)
- Transcodificación automática a G.711/Opus
- Transmisión RTP bidireccional

### Monitoreo de Trunks
- Keep-alive mediante OPTIONS
- Detección automática de caídas
- Estadísticas de disponibilidad

## 📋 Requisitos

### Sistema Operativo
- Linux (Ubuntu/Debian/CentOS recomendado)

### Software
- Node.js v14+
- Librerías SIP y RTP
- Docker (opcional)

## 🚀 Instalación

```bash
# Clonar el repositorio
git clone https://github.com/tzootz/siptester-gui.git

# Instalar dependencias del backend
cd siptester-gui/backend
npm install

# Instalar dependencias del frontend
cd ../frontend
npm install

# Iniciar la aplicación
npm run dev
```

## 📖 Guía de Uso

1. **Configuración Inicial**
   - Configurar IP/puerto del servidor SIP
   - Establecer parámetros de OPTIONS
   - Seleccionar códec preferido

2. **Preparación de Audio**
   - Subir archivo de audio para pruebas
   - Verificar la codificación

3. **Generación de Tráfico**
   - Definir número de llamadas simultáneas
   - Establecer tasa de llamadas por segundo
   - Iniciar generación de tráfico

4. **Monitoreo**
   - Observar estados de llamadas
   - Revisar estadísticas en tiempo real
   - Verificar estado del trunk

## 🔧 Configuración

```yaml
# Ejemplo de configuración (config.yaml)
sip:
  host: "192.168.1.100"
  port: 5060
  transport: "tcp"

monitoring:
  options_interval: 10
  call_rate: 10
  max_concurrent_calls: 100

audio:
  codec: "G711"
  input_file: "test.mp3"
```

## 🎯 Casos de Uso

- **Pruebas de Carga**: Validación de capacidad de PBX
- **Monitoreo de Trunks**: Supervisión continua de disponibilidad
- **Pruebas de Audio**: Validación de calidad y transcodificación
- **Simulación de Tráfico**: Generación de escenarios realistas

## 🤝 Contribución

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add: Amazing Feature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE.md](LICENSE.md) para más detalles.

## 👥 Autores

- **[TZOOTZ RESEARCH]** - *SIP GENERATOR* - [TuGitHub](https://github.com/tzootz)

## 🙏 Idea original de Jerónimo Mosquera

- PJSIP por su excelente stack SIP
- La comunidad de VoIP por su continuo apoyo
