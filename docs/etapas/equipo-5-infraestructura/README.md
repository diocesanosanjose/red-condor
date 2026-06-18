# Equipo 5: Infraestructura

**Objetivo:** Analizar como almacenar, procesar y visualizar la informacion generada por el sistema.

## Flujo de informacion

Los datos generados por los dispositivos en campo deben ser recibidos, almacenados y presentados de forma util para los usuarios finales.

```
Dispositivos en campo --> Gateway --> Servidor --> Base de datos --> Aplicacion web
     (LoRa)              (Internet)   (Procesamiento)  (Almacenamiento)  (Visualizacion)
```

## Temas a investigar

| Tema | Que hay que responder |
|------|----------------------|
| **Servidores** | ?Que es un servidor? ?Que hardware minimo necesita Red Condor? ?Se puede usar una PC reciclada? ?Que SO usar (Linux, Windows)? ?Que es Docker? |
| **Bases de datos** | ?Que tipos de bases de datos existen (SQL vs NoSQL)? ?Que es InfluxDB (series temporales)? ?Como se almacenan datos de sensores y GPS? |
| **Aplicaciones web** | ?Como se crea un dashboard para visualizar datos? ?Que es Grafana? ?Como se accede desde cualquier dispositivo? |
| **Monitoreo** | ?Como se generan alertas en tiempo real? ?Que es MQTT? ?Que es Node-RED? ?Como se envia una alerta por email o Telegram? |

## Actividades

1. Investigar cada tema con fuentes confiables
2. Elaborar un resumen en `investigacion.md`
3. Identificar dudas en `preguntas-abiertas.md`
4. Proponer aplicaciones para Red Condor en `propuestas.md`
5. Compartir hallazgos con el resto del curso
