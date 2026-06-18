# Equipo 5: Infraestructura

**Objetivo:** Analizar cómo almacenar, procesar y visualizar la información generada por el sistema.

## Flujo de información

Los datos generados por los dispositivos en campo deben ser recibidos, almacenados y presentados de forma útil para los usuarios finales.

```
Dispositivos en campo --> Gateway --> Servidor --> Base de datos --> Aplicación web
     (LoRa)              (Internet)   (Procesamiento)  (Almacenamiento)  (Visualización)
```

## Temas a investigar

| Tema | Qué hay que responder |
|------|----------------------|
| **Servidores** | ¿Qué es un servidor? ¿Qué hardware mínimo necesita Red Condor? ¿Se puede usar una PC reciclada? ¿Qué SO usar (Linux, Windows)? ¿Qué es Docker? |
| **Bases de datos** | ¿Qué tipos de bases de datos existen (SQL vs NoSQL)? ¿Qué es InfluxDB (series temporales)? ¿Cómo se almacenan datos de sensores y GPS? |
| **Aplicaciones web** | ¿Cómo se crea un dashboard para visualizar datos? ¿Qué es Grafana? ¿Cómo se accede desde cualquier dispositivo? |
| **Monitoreo** | ¿Cómo se generan alertas en tiempo real? ¿Qué es MQTT? ¿Qué es Node-RED? ¿Cómo se envía una alerta por email o Telegram? |

## Actividades

1. Investigar cada tema con fuentes confiables
2. Elaborar un resumen en `investigacion.md`
3. Identificar dudas en `preguntas-abiertas.md`
4. Proponer aplicaciones para Red Condor en `propuestas.md`
5. Compartir hallazgos con el resto del curso
