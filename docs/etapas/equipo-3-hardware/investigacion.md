# Investigacion1. Introducción
Este documento detalla los hallazgos técnicos sobre el hardware necesario para construir los nodos de la Red Cóndor en Malargüe
. Debido a que el proyecto se encuentra en fase de diseño conceptual, esta investigación es la base para la adquisición de los primeros prototipos de la Etapa 1
.
2. Componentes Principales
2.1 Microcontrolador: ESP32
Se ha identificado al ESP32 como el "cerebro" ideal para los nodos de la red
.
Capacidades: Posee un procesador de doble núcleo con conectividad WiFi y Bluetooth integrada, superando ampliamente a las placas Arduino tradicionales en potencia y versatilidad [fuente externa].
Uso en el proyecto: Es compatible con el ecosistema Meshtastic que se planea implementar para la red mesh
.
Costo: Es una solución económica y de alta disponibilidad en el mercado regional.
2.2 Sensores Ambientales
Para cumplir con el objetivo de la Etapa 6 (Telemetría ambiental), se integrarán sensores climáticos
.
Modelos evaluados: El sensor BME280 es el más recomendado por su capacidad de medir temperatura, humedad y presión atmosférica mediante el protocolo I2C (solo 2 cables de datos) [fuente externa].
Consumo: Son componentes diseñados para operar con bajo consumo, fundamentales para los repetidores solares autónomos
.
2.3 Módulo GPS
Fundamental para los nodos móviles de los puesteros y crianceros
.
Propósito: Proporcionar coordenadas exactas en los mensajes de texto y alertas de emergencia
.
Rendimiento: Se deben priorizar módulos con Hot Start rápido para minimizar el consumo de batería en campo [fuente externa].
Compatibilidad: Módulos tipo NEO-6M o similares son estándares para conectar con el ESP32
.
3. Protección y Carcasas
Dado que el despliegue es en zonas de montaña con condiciones extremas de nieve, viento y frío
, la protección física es crítica.
Estándar IP67: Se busca que las carcasas garanticen estanqueidad total frente al polvo y resistencia a la inmersión temporal en agua [fuente externa].
Materiales: Se recomiendan materiales como el ABS o ASA para la impresión 3D de las carcasas, ya que resisten mejor los rayos UV y las temperaturas de hasta -20°C que el plástico común [3, fuente externa].
4. Estado Actual y Próximos Pasos
Actualmente no se ha comprado hardware
. El siguiente paso para este equipo es definir la lista de materiales (BOM) para la Prueba de Concepto, asegurando la compatibilidad con el sistema de energía solar que diseñará el Equipo 2
.

