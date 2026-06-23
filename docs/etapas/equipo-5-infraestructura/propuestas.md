# Propuestas para Red Condor Infraestructura

## Arquitectura Recomendada
1. **Gateway (Bardas Blancas + redundantes)**: PC reciclada + Docker Compose con:
   - Meshtastic Python API (recepción LoRa)
   - Mosquitto MQTT
   - Node-RED (lógica y alertas)
   - InfluxDB (almacenamiento local)
   - Grafana (visualización local)

2. **Servidor Central (Colegio San José)**: Recibe vía MQTT/Tailscale, consolida datos, dashboards principales y escalamiento de alertas.

3. **Flujo de Datos**:
   - Nodo LoRa → Gateway → MQTT → Node-RED → InfluxDB + Alertas (Telegram/Email)
   - Grafana consume InfluxDB para mapas de posición, telemetría de batería, cobertura RF (RSSI/SNR).

## Beneficios Educativos
- **Estudiantes**: Aprenden Docker, Linux CLI, flujos visuales, bases de series temporales, visualización de datos reales.
- **Integración**: Dashboard con mapa de cobertura, estado de nodos, historial de alertas.

## Próximos Pasos Propuestos (Etapa 4)
- Instalar Docker + Compose en servidor de pruebas.
- Probar stack completo con datos simulados de Meshtastic.
- Crear docker-compose.yml base (documentar en repo).
- Dashboard MVP: Mapa GPS + medidores de batería + tabla de últimos mensajes.

Esta propuesta es **resiliente** (almacenamiento local en gateways) y **escalable**, alineada con las Hipótesis y Capas del documento de contexto.
