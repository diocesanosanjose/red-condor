1. Plataforma Base: ESP32 + LoRa
¿Qué es el ESP32?: Es un microcontrolador de bajo costo y muy bajo consumo de energía que incluye Wi-Fi y Bluetooth. En este proyecto, se combina con un chip LoRa para permitir la comunicación a larga distancia
.
Módulos considerados: Se evalúan dispositivos como el Lilygo T-Beam o T-Echo. El T-Beam es muy usado porque ya integra el ESP32, el chip LoRa y un módulo GPS en una sola placa
.
2. Posicionamiento: GPS en la Montaña
Función: El GPS permite obtener las coordenadas exactas (latitud y longitud) del puestero. Esta información se envía por la red LoRa para que, en caso de emergencia, se sepa dónde buscar
.
Desafío: En los cañones profundos de Malargüe, la señal de los satélites puede ser difícil de captar. Por eso, el hardware debe tener una antena GPS con buena sensibilidad
.
3. Sensores Adicionales
Tipos: Aunque el foco inicial es la alerta de emergencia, en etapas avanzadas (Etapa 6) se planea agregar sensores de temperatura, humedad y presión atmosférica para generar telemetría climática
.
Conexión: Estos sensores suelen usar protocolos de comunicación como I2C o SPI, que el ESP32 maneja fácilmente
.
4. Protección Física: Carcasas y Estanqueidad
IP67: Los dispositivos deben estar protegidos por cajas estancas con certificación mínima IP67 (protección total contra polvo y resistencia a inmersión en agua). Esto es vital para soportar la nieve y el "viento blanco"
.
Resistencia térmica: El hardware debe operar en un rango extremo, desde el calor del verano hasta los -20°C en invierno
.
5. Interfaz de Usuario
Botón de SOS: El diseño debe incluir un botón físico de emergencia que sea fácil de presionar incluso con guantes o en condiciones de frío extremo
.

