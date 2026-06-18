# Red Cóndor -- Red Rural Autónoma de Comunicaciones y Alertas

Proyecto educativo y comunitario del **Colegio Diocesano San José** (Malargüe, Mendoza, Argentina) que busca diseñar, construir y operar una red rural autónoma de comunicaciones y alertas basada en tecnología **LoRa/Meshtastic** para zonas de montaña del departamento de Malargüe.

## El problema

Puesteros y crianceros de la zona de Bardas Blancas y corredores aledaños quedan incomunicados durante temporales invernales, con antecedentes de fallecidos por no poder pedir ayuda. Las comunicaciones celulares no tienen cobertura en la mayoría del territorio rural.

## La solución

Red mesh de radios LoRa de bajo consumo, con:
- **Nodos móviles** para los puesteros (botón de alerta + GPS + mensajes de texto)
- **Gateways fijos** con conexión a internet satelital o rural
- **Repetidores solares autónomos** en puntos elevados
- **Servidor central** en el Colegio San José que recibe, procesa y distribuye las alertas

## Estado

**Fase de diseño conceptual.** No se ha comprado hardware. No se han realizado pruebas RF de campo. La infraestructura escolar base está operativa.

## Etapas

| Etapa | Objetivo | Estado |
|-------|----------|--------|
| 0 -- Fundamentos | Marco institucional, simulación RF, repositorio | En progreso |
| 1 -- Prueba de concepto | 2 nodos funcionando con Meshtastic | Pendiente |
| 2 -- Mapeo urbano | Caracterizar RF en Malargüe | Pendiente |
| 3 -- Pruebas rurales | Cobertura en corredor Bardas Blancas | Pendiente |
| 4 -- Gateway | Conectar red LoRa al servidor San José | Pendiente |
| 5 -- Repetidores solares | Extender cobertura | Pendiente |
| 6 -- Sensores climáticos | Telemetría ambiental | Pendiente |
| 7 -- Plataforma avanzada | Alertas automáticas y mapas | Pendiente |

## Equipos de investigación (Etapa 0)

| Equipo | Área | Carpeta |
|--------|------|---------|
| 1 | Comunicaciones (LoRa, antenas, cobertura) | `docs/etapas/equipo-1-comunicaciones/` |
| 2 | Energía (paneles solares, baterías, autonomía) | `docs/etapas/equipo-2-energia/` |
| 3 | Hardware (ESP32, sensores, GPS, carcasas) | `docs/etapas/equipo-3-hardware/` |
| 4 | Usuarios (puesteros, rescatistas, necesidades) | `docs/etapas/equipo-4-usuarios/` |
| 5 | Infraestructura (servidores, bases de datos, monitoreo) | `docs/etapas/equipo-5-infraestructura/` |

Ver [docs/etapas/etapa-0-organizacion-equipos.md](docs/etapas/etapa-0-organizacion-equipos.md) para la guía completa.

## Estructura del repositorio

```
red-condor/
├── README.md                   # Este archivo
├── docs/
│   ├── contexto/               # Documentos de contexto y versiones
│   ├── etapas/                 # Informes de cada etapa
│   ├── hardware/               # Fichas técnicas de cada nodo
│   ├── servidor/               # Configuración, servicios, backups
│   ├── protocolos/             # Procedimientos operativos
│   └── decisiones/             # Registro de decisiones (ADR)
├── firmware/                   # Versiones de firmware y configuraciones
├── software/                   # Scripts, flows Node-RED, docker-compose
├── mapas/                      # Archivos GIS, mapas de cobertura RF
├── fotos/                      # Instalaciones, pruebas de campo
└── protocolos/                 # Procedimientos operativos detallados
```

## Institución

**Colegio Diocesano San José** -- Malargüe, Mendoza, Argentina

Autor: Paulo Alvarez · alvarezpaulo82@gmail.com

## Licencia

Por definir.
