# Investigación Infraestructura - Santiago Balverdi

Red Cóndor: Infraestructura Tecnológica y Lógica de Datos
1. Servidores y Hardware
¿Qué es un servidor?: En este proyecto, el servidor actúa como el "Cerebro" o la capa de procesamiento y lógica
. Recibe los datos de los gateways, los procesa según reglas predefinidas y decide si debe disparar una alerta
.
Hardware mínimo:
Gateway/Servidor local: Procesador Intel i5-3320M, 4 GB de RAM y 120 GB de disco SSD
. Requiere una UPS de 600-1000 VA para resiliencia eléctrica
.
Nodos de campo: Placas ESP32 con LoRa (como T-Beam), baterías 18650 y, en repetidores, baterías LiFePO4 con paneles solares de 10-20W
.
¿Se puede usar una PC reciclada?: Sí. El diseño contempla específicamente el uso de hardware reciclado para el gateway de Bardas Blancas, lo que reduce costos y facilita la implementación en zonas rurales
.
Sistema Operativo: Se utiliza Linux, específicamente la distribución Debian 12 (Bookworm) por ser una versión estable y con soporte a largo plazo (LTS)
. No se utiliza Windows debido a la necesidad de estabilidad y gestión de contenedores
.
¿Qué es Docker?: Es una herramienta de contenedorización que permite empaquetar servicios (como Node-RED o InfluxDB) de forma aislada
. Esto facilita que el sistema sea reproducible, fácil de actualizar por los alumnos y resistente a errores de configuración
.
2. Bases de Datos
Tipos de bases de datos: Aunque existen las SQL (relacionales, como MySQL) y NoSQL (no relacionales, como MongoDB), este proyecto se centra en las de series temporales
. (Nota: La distinción general SQL vs NoSQL no está detallada en las fuentes, pero es información técnica estándar).
InfluxDB: Es una base de datos de series temporales (TSDB) utilizada para almacenar telemetría histórica
. Es ideal para registrar datos que cambian en el tiempo, como el voltaje de una batería o la temperatura
.
Almacenamiento de sensores y GPS: Los datos recibidos por LoRa se envían a través de un bus de mensajes (MQTT) hacia InfluxDB
. Se guardan campos como battery_level, gps_satellites y la posición geográfica para seguimiento en caso de emergencia
.
3. Aplicaciones Web y Visualización
¿Cómo se crea un dashboard?: Se utiliza la herramienta Grafana conectada a InfluxDB
. Grafana consulta los datos almacenados y los transforma en gráficos, indicadores de nivel y mapas de calor
.
¿Qué es Grafana?: Es la plataforma de visualización que permite ver el estado de salud de toda la red de un vistazo (por ejemplo, qué nodos están online o tienen batería baja)
.
Acceso desde dispositivos: Se accede mediante un navegador web. Para garantizar la seguridad, el acceso está restringido a la red privada Tailscale (VPN), lo que permite que los alumnos y docentes vean los datos desde cualquier lugar de forma cifrada sin exponer el servidor a internet abierto
.
4. Monitoreo y Alertas
Generación de alertas: Ocurre en la capa de procesamiento mediante reglas de umbral (ejemplo: "si la batería < 20%, avisar")
.
MQTT: Es el protocolo de mensajería (bus de datos) que permite que los distintos programas del servidor se comuniquen entre sí de forma eficiente y ligera
.
Node-RED: Es una herramienta de programación visual basada en flujos
. Se encarga de la lógica de reenvío: recibe el mensaje de MQTT, lo transforma y lo envía al destino final (Telegram, Email)
.
Envío por Telegram/Email: Node-RED se conecta a las APIs de estos servicios. Cuando se detecta una señal de auxilio, el sistema dispara automáticamente el mensaje al grupo de emergencia configurado
.
Resumen para GitHub
El proyecto Red Cóndor utiliza un stack tecnológico moderno y eficiente:
Hardware: PC recicladas con Linux Debian y microcontroladores ESP32 con LoRa
.
Infraestructura: Servicios orquestados mediante Docker para asegurar la sostenibilidad educativa
.
Flujo de Datos: Los datos viajan por MQTT, se almacenan en InfluxDB y se visualizan en Grafana
.
Inteligencia: Node-RED gestiona la lógica de las alertas críticas, enviando notificaciones en tiempo real a las autoridades competentes
.

