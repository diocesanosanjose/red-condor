# Preguntas abiertas Infraestructura

## Servidores y Hardware
- ¿La PC reciclada i5-3320M con 4 GB RAM soporta bien la carga de 2-3 gateways + telemetría? ¿Necesitamos subir a 8 GB?
- ¿Hay UPS suficiente en el Colegio San José y Bardas Blancas? ¿Autonomía real en cortes?
- ¿El servidor escolar puede correr todo en Docker sin afectar otros servicios educativos?

## Bases de Datos
- ¿Cuántos nodos/repetidores generarán datos diarios? ¿InfluxDB maneja bien el volumen inicial + futuro escalado?
- Política de retención: ¿Cómo configuramos borrado automático de posiciones GPS después de 90 días?

## Dashboards y Acceso
- ¿Acceso seguro desde internet (Tailscale VPN)? ¿O solo LAN/VPN?
- ¿Necesitamos dashboard público (solo lectura) para autoridades o solo interno?

## Monitoreo y Alertas
- ¿Cómo integramos Node-RED con Meshtastic Python API para alertas de botón de pánico?
- ¿Qué canales de notificación priorizar (Telegram prioritario para Defensa Civil)?
- ¿Cómo evitar alertas duplicadas si múltiples gateways reciben el mismo mensaje?

## Generales
- ¿Disponibilidad de internet rural estable en ubicaciones de gateways redundantes?
- ¿Capacitación: los estudiantes de Equipo 5 pueden instalar/configurar este stack en Etapa 4?
