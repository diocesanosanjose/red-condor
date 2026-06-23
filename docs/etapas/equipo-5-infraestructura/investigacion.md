# Investigación Infraestructura

## Servidores
- **¿Qué es un servidor?** Computadora (o conjunto de ellas) que proporciona servicios a otros dispositivos en red (almacenamiento de datos, procesamiento, hosting de aplicaciones).
- **Hardware mínimo para Red Cóndor**: PC reciclada como la mencionada (i5-3320M, 4 GB RAM, SSD 120 GB) es viable. Docker reduce el consumo. Recomendación: mínimo 4-8 GB RAM y CPU de 2+ núcleos para correr contenedores (Meshtastic API, MQTT, Node-RED, InfluxDB, Grafana).
- **SO recomendado**: Debian 12 (Bookworm) LTS — estable, bajo consumo, excelente soporte Docker.
- **Docker**: Tecnología de contenedores que empaqueta aplicaciones con sus dependencias. Permite deployment fácil, actualizaciones y aislamiento. Ideal para el gateway y servidor escolar (evita conflictos).

## Bases de Datos
- **SQL vs NoSQL**: SQL (estructurado, transacciones) vs NoSQL (flexible, escalable). Para Red Cóndor: **Time Series DB** (NoSQL optimizada para datos temporales).
- **InfluxDB**: Base de datos de series temporales perfecta para telemetría IoT (GPS, batería, RSSI, sensores climáticos). Almacena datos con timestamp, tags (ej: nodo_id, location) y fields (valor). Alta tasa de ingestión, compresión eficiente y queries rápidas. Soporta modo offline (local en gateway).

## Aplicaciones Web / Dashboards
- **Grafana**: Herramienta open-source líder para visualización. Crea dashboards interactivos con gráficos, mapas (GPS), alertas y paneles en tiempo real. Se conecta fácilmente a InfluxDB. Accesible desde cualquier dispositivo (PC, móvil) vía web.

## Monitoreo y Alertas
- **MQTT**: Protocolo ligero de mensajería publish/subscribe. Ideal para LoRa → Gateway (bajo ancho de banda, confiable en redes inestables).
- **Mosquitto**: Broker MQTT popular, liviano y confiable. Se instala en Docker.
- **Node-RED**: Herramienta de flujos visuales (low-code). Recibe datos MQTT, procesa (reglas de alerta), guarda en InfluxDB y envía notificaciones (email, Telegram). Perfecto para lógica de emergencia.

**Fuentes principales**: Documentación oficial (InfluxData, Grafana, Node-RED), tutoriales IoT con ESP32/LoRa y casos de uso en monitoreo remoto.<grok-card data-id="5ccccb" data-type="citation_card" data-plain-type="render_inline_citation" ></grok-card>

**Conclusión para Red Cóndor**: Stack completo open-source: Meshtastic → MQTT (Mosquitto) → Node-RED → InfluxDB → Grafana. Resiliente (modo offline) y educativo (estudiantes aprenden Docker, Linux, flujos).

