# Red Condor -- Red Rural Autonoma de Comunicaciones y Alertas

Proyecto educativo y comunitario del **Colegio Diocesano San Jose** (Malargue, Mendoza, Argentina) que busca disenar, construir y operar una red rural autonoma de comunicaciones y alertas basada en tecnologia **LoRa/Meshtastic** para zonas de montana del departamento de Malargue.

## El problema

Puesteros y crianceros de la zona de Bardas Blancas y corredores aledaños quedan incomunicados durante temporales invernales, con antecedentes de fallecidos por no poder pedir ayuda. Las comunicaciones celulares no tienen cobertura en la mayoria del territorio rural.

## La solucion

Red mesh de radios LoRa de bajo consumo, con:
- **Nodos moviles** para los puesteros (boton de alerta + GPS + mensajes de texto)
- **Gateways fijos** con conexion a internet satelital o rural
- **Repetidores solares autonomos** en puntos elevados
- **Servidor central** en el Colegio San Jose que recibe, procesa y distribuye las alertas

## Estado

**Fase de diseno conceptual.** No se ha comprado hardware. No se han realizado pruebas RF de campo. La infraestructura escolar base esta operativa.

## Etapas

| Etapa | Objetivo | Estado |
|-------|----------|--------|
| 0 -- Fundamentos | Marco institucional, simulacion RF, repositorio | En progreso |
| 1 -- Prueba de concepto | 2 nodos funcionando con Meshtastic | Pendiente |
| 2 -- Mapeo urbano | Caracterizar RF en Malargue | Pendiente |
| 3 -- Pruebas rurales | Cobertura en corredor Bardas Blancas | Pendiente |
| 4 -- Gateway | Conectar red LoRa al servidor San Jose | Pendiente |
| 5 -- Repetidores solares | Extender cobertura | Pendiente |
| 6 -- Sensores climaticos | Telemetria ambiental | Pendiente |
| 7 -- Plataforma avanzada | Alertas automaticas y mapas | Pendiente |

## Estructura del repositorio

```
red-condor/
├── README.md                   # Este archivo
├── docs/
│   ├── contexto/               # Documentos de contexto y versiones
│   ├── etapas/                 # Informes de cada etapa
│   ├── hardware/               # Fichas tecnicas de cada nodo
│   ├── servidor/               # Configuracion, servicios, backups
│   ├── protocolos/             # Procedimientos operativos
│   └── decisiones/             # Registro de decisiones (ADR)
├── firmware/                   # Versiones de firmware y configuraciones
├── software/                   # Scripts, flows Node-RED, docker-compose
├── mapas/                      # Archivos GIS, mapas de cobertura RF
├── fotos/                      # Instalaciones, pruebas de campo
└── protocolos/                 # Procedimientos operativos detallados
```

## Institucion

**Colegio Diocesano San Jose** -- Malargue, Mendoza, Argentina

Autor: Paulo Alvarez · alvarezpaulo82@gmail.com

## Licencia

Por definir.
