# Red Cóndor — Red Rural Autónoma de Comunicaciones y Alertas

## Documento de Contexto Integral — Versión 5.0

> **Propósito de este documento:** Servir como contexto completo y actualizado para
> análisis con inteligencia artificial, discusión con tomadores de decisiones humanos
> y base institucional para el diseño, implementación y evolución del proyecto.
>
> Este documento no es un plan de proyecto cerrado. Es un mapa vivo de lo que se sabe,
> lo que no se sabe, lo que se hipotetiza y lo que se debe validar.

---

**Proyecto:** Red Cóndor
**Institución:** Colegio Diocesano San José — Malargüe, Mendoza, Argentina
**Autor:** Paulo Alvarez · alvarezpaulo82@gmail.com
**Versión:** 5.0 — Junio 2026
**Estado:** Diseño conceptual con hipótesis no validadas. Previo a compra de hardware.

---

# Índice

1. [Resumen Ejecutivo](#1-resumen-ejecutivo)
2. [Contexto Territorial y Humano](#2-contexto-territorial-y-humano)
3. [El Problema](#3-el-problema)
4. [Lo Que NO Es el Proyecto](#4-lo-que-no-es-el-proyecto)
5. [Hipótesis Críticas](#5-hipótesis-críticas)
6. [Arquitectura del Sistema por Capas](#6-arquitectura-del-sistema-por-capas)
7. [Componentes Técnicos](#7-componentes-técnicos)
8. [Diseño Energético del Nodo del Puestero](#8-diseño-energético-del-nodo-del-puestero)
9. [Protocolo de Emergencia y Coordinación Institucional](#9-protocolo-de-emergencia-y-coordinación-institucional)
10. [Redundancia y Resiliencia de Infraestructura](#10-redundancia-y-resiliencia-de-infraestructura)
11. [Gobernanza y Marco Institucional](#11-gobernanza-y-marco-institucional)
12. [Sostenibilidad del Proyecto](#12-sostenibilidad-del-proyecto)
13. [Modelo Educativo y Participación Estudiantil](#13-modelo-educativo-y-participación-estudiantil)
14. [Estrategia de Documentación y Repositorio](#14-estrategia-de-documentación-y-repositorio)
15. [Plan de Implementación por Etapas](#15-plan-de-implementación-por-etapas)
16. [Plan de Expansión Territorial](#16-plan-de-expansión-territorial)
17. [Análisis de Riesgos](#17-análisis-de-riesgos)
18. [Métricas de Validación y Telemetría](#18-métricas-de-validación-y-telemetría)
19. [Integración con Radioafición y APRS](#19-integración-con-radioafición-y-aprs)
20. [Antecedentes, Alianzas e Instituciones Relacionadas](#20-antecedentes-alianzas-e-instituciones-relacionadas)
21. [Registro de Decisiones Abiertas](#21-registro-de-decisiones-abiertas)
22. [Hoja de Ruta y Próximas Acciones](#22-hoja-de-ruta-y-próximas-acciones)

---

# 1. Resumen Ejecutivo

Red Cóndor es un proyecto educativo y comunitario que busca diseñar, construir y operar
una red rural autónoma de comunicaciones y alertas basada en tecnología LoRa/Meshtastic
para zonas de montaña del departamento de Malargüe, Mendoza, Argentina.

El proyecto nace de un problema real y documentado: puesteros y crianceros de la zona
de Bardas Blancas y corredores aledaños quedan incomunicados durante temporales
invernales, con antecedentes de fallecidos por no poder pedir ayuda.

La solución propuesta es una red mesh de radios LoRa de bajo consumo, con nodos móviles
para los puesteros, gateways fijos con conexión a internet satelital o rural, repetidores
solares autónomos en puntos elevados, y un servidor central en el Colegio San José que
recibe, procesa y distribuye las alertas.

El proyecto se distingue por:

- No inventar un problema para justificar la tecnología. El problema existe y tiene
  consecuencias letales.
- Aprovechar infraestructura digital existente (servidor escolar, Tailscale, Nextcloud,
  monitoreo) en lugar de construir todo desde cero.
- Tener una estructura institucional pensada (cláusula de patrocinio, política de datos,
  acta de creación pendiente).
- Estar anclado en un territorio con características excepcionales para RF (baja
  contaminación, relieve desafiante, infraestructura científica internacional presente).
- Tener un enfoque educativo real basado en Linux, Docker, RF, GIS, MQTT, energía solar
  y redes, no en "aprendamos Arduino".

**Estado actual:** Fase de diseño conceptual. No se ha comprado hardware. No se han
realizado pruebas RF de campo. La infraestructura escolar base está operativa.

**Inversión inicial estimada (Etapa 1):** USD 80-150.

---

# 2. Contexto Territorial y Humano

## 2.1 Malargüe como territorio

Malargüe es el departamento más austral de la provincia de Mendoza, con una densidad
de población extremadamente baja (aproximadamente 30.000 habitantes en 41.000 km²).
Su economía se basa en la ganadería extensiva caprina y bovina, la minería, el turismo
de nieve (Las Leñas) y la infraestructura científica internacional (Observatorio Pierre
Auger, DS3 de ESA/CONAE).

El relieve es montañoso, con valles profundos, cañones y una Cordillera de los Andes
que supera los 4.000 msnm. Las rutas rurales son mayoritariamente de ripio o huella,
y muchas zonas quedan intransitables en invierno.

## 2.2 El ciclo anual del puestero

Esta sección documenta lo que se sabe y lo que NO se sabe sobre el ciclo de actividad
de los puesteros en la montaña. Esta información es crítica porque define:

- En qué meses el sistema debe estar operativo.
- Cuánto tiempo debe durar la batería de un nodo sin recarga.
- Si se necesita panel solar portátil o basta con una batería más grande.
- Cuándo se puede hacer mantenimiento de infraestructura en el campo.

### Lo que se sabe (aproximación regional)

En la región andina mendocina, la ganadería de montaña sigue un ciclo estacional
conocido como **veranada e invernada**:

| Temporada | Meses típicos | Actividad del puestero |
|-----------|---------------|------------------------|
| **Veranada** (subida a la montaña) | Noviembre a abril | Los puesteros suben con el ganado cuando la nieve se derrite en los pasos y los pastos de altura están disponibles. |
| **Invernada** (bajada al valle) | Mayo a octubre | El ganado baja a zonas más cálidas y bajas. Los puesteros no arream en la montaña. |

### Lo que NO se sabe y debe averiguarse

> **Preguntas abiertas prioritarias:**

> 1. ¿Hay puesteros que realizan actividad en la montaña durante mayo y octubre,
>    o el corte entre veranada e invernada es abrupto?
>
> 2. ¿Hay puesteros que realizan recorridas cortas (1-3 días) durante el invierno
>    para verificar aguadas o infraestructura?
>
> 3. ¿Cuánto tiempo permanece un puestero en la montaña de forma continua durante
>    la veranada? ¿Días, semanas, meses? ¿Sube y baja frecuentemente o se queda
>    temporadas largas?
>
> 4. ¿Existe diferencia significativa entre las zonas de Bardas Blancas, Las Loicas
>    y el corredor del Pehuenche en cuanto a calendario de actividad?
>
> 5. ¿La directora del Colegio San José o algún docente tiene contacto directo con
>    puesteros de Bardas Blancas que pueda precisar estas fechas?

### Implicancias de diseño

| Escenario | Implicancia |
|-----------|-------------|
| El puestero sube **semanas seguidas** sin bajar | Necesita panel solar portátil o batería externa de gran capacidad (10.000+ mAh). |
| El puestero sube y baja **cada 2-3 días** | Una batería 18650 (3.000 mAh) en modo ahorro puede ser suficiente. Recarga en el puesto. |
| El puestero **no usa el nodo en invierno** | El sistema tiene una "ventana de mantenimiento" de mayo a octubre para reparar nodos y gateways. |
| Hay actividad parcial **en mayo y octubre** | El sistema debe estar operativo desde octubre hasta abril, con posible extensión. |

## 2.3 Zonas de intervención priorizadas

El proyecto identifica las siguientes zonas como potenciales corredores de expansión.
La priorización es una hipótesis inicial que debe ser validada con criterios objetivos:

| Prioridad | Zona / Localidad | Perfil | Justificación |
|-----------|------------------|--------|---------------|
| **1** | Bardas Blancas | Puesteros, veranada rural | Zona piloto. Antecedentes de emergencias. Cercanía relativa a Malargüe. |
| **2** | Las Loicas | Gendarmería, Aduana, paso internacional | Presencia institucional permanente. Infraestructura existente. |
| **3** | Real del Pehuenche | Paso internacional | Corredor estratégico. Tránsito estacional. |
| **4** | Cajón Grande | Rural / veranada | Conecta con Bardas Blancas. Zona de puesteros. |
| **5** | Valle Hermoso | Rural / turismo | Acceso a zona termal. Población dispersa. |
| **6** | Los Molles | Turismo termal | Infraestructura turística. Potencial económico. |
| **7** | Las Leñas | Turismo de nieve | Perfil diferente (turismo, no emergencia rural). Evaluar pertinencia. |

> **Preguntas abiertas de priorización:**
>
> ¿Qué corredor tiene mayor riesgo humano real (antecedentes de fallecidos,
> accidentes, aislamiento)?
>
> ¿Dónde existe mejor infraestructura existente (energía, internet, edificio
> seguro) para instalar un gateway?
>
> ¿Cuál es la segunda zona después de Bardas Blancas que debería priorizarse,
> según la percepción de la comunidad y las autoridades?

---

# 3. El Problema

## 3.1 Antecedentes reales

En la zona de Bardas Blancas y corredores rurales de Malargüe existen antecedentes
documentados de puesteros fallecidos durante temporales invernales por no poder
comunicar su situación ni solicitar ayuda. Las condiciones climáticas extremas de la
región (nevadas, viento blanco, temperaturas de -20°C) aíslan completamente a las
personas en la montaña durante días o semanas.

Las comunicaciones celulares no tienen cobertura en la mayoría del territorio rural
de Malargüe. Las radios VHF existen pero no son universales, requieren licencia en
muchos casos, y no todos los puesteros tienen acceso a ellas ni conocimiento para
usarlas en emergencia.

## 3.2 Por qué esto no es un problema inventado

El proyecto no parte de una tecnología buscando problema. Parte de:

- Un territorio con **aislamiento real y documentado**.
- Actividades económicas (ganadería de montaña) que **obligan a las personas a
  estar en zonas sin comunicación**.
- **Antecedentes fatales** que demuestran que la falta de comunicación mata.
- **Condiciones climáticas extremas** que agravan cualquier emergencia.
- **Ausencia de alternativa tecnológica accesible** para la población rural de
  bajos recursos.

---

# 4. Lo Que NO Es el Proyecto

Esta sección es tan importante como la descripción del proyecto. Define límites
claros de alcance, responsabilidad y capacidades. Protege institucionalmente al
Colegio San José, a los estudiantes y a los usuarios.

Red Cóndor **NO**:

- **No reemplaza a Defensa Civil, Gendarmería ni ningún servicio de emergencia
  profesional.** El proyecto es una capa adicional de comunicación, no un sistema
  de respuesta a emergencias.
- **No garantiza cobertura total del territorio.** La cobertura depende de la
  topografía, la cantidad de repetidores instalados y las condiciones climáticas.
  Habrá zonas sin señal.
- **No reemplaza la radio VHF profesional ni los sistemas satelitales (Garmin,
  Iridium).** Para emergencias graves en zonas sin cobertura LoRa, los medios
  tradicionales siguen siendo necesarios.
- **No es un sistema certificado de rescate.** Las alertas que emite el sistema
  no tienen garantía de entrega ni de tiempo de respuesta.
- **No garantiza la entrega absoluta de mensajes.** La red LoRa es "best effort".
  Factores ambientales, de batería o de infraestructura pueden impedir la entrega.
- **No es un negocio ni un servicio comercial.** Es un proyecto educativo y
  comunitario sin fines de lucro.
- **No reemplaza la preparación personal para condiciones climáticas extremas.**
  El sistema complementa, no sustituye, las prácticas de seguridad tradicionales
  de los puesteros.
- **No recopila datos para fines de vigilancia, control gubernamental ni uso
  comercial.** Los datos GPS y de mensajes tienen fines exclusivos de emergencia
  y mejora técnica del sistema.

---

# 5. Hipótesis Críticas

Todo proyecto serio explicita sus hipótesis. Cada hipótesis aquí listada debe ser
validada o refutada antes de que el proyecto avance a la siguiente fase. Si una
hipótesis crítica resulta falsa, el diseño del proyecto debe ajustarse.

| # | Hipótesis | Estado | Cómo se valida | Impacto si es falsa |
|---|-----------|--------|----------------|---------------------|
| H1 | LoRa/Meshtastic tendrá cobertura útil (>1 km) en el corredor Bardas Blancas | No validado | Prueba de campo con 2 nodos en el corredor real (Etapa 3) | El proyecto necesita repetidores adicionales o cambia de tecnología |
| H2 | Un nodo móvil puede operar 3-5 días sin recarga en modo de bajo consumo | Parcialmente validado (datos de terceros) | Prueba de autonomía real con el hardware específico (Etapa 1) | Se necesita panel solar portátil o batería externa |
| H3 | Los puesteros aceptarán usar el sistema y lo llevarán consigo a la montaña | No validado | Prueba piloto con 2-3 puesteros durante una temporada (Etapa 3+) | El proyecto debe rediseñar interfaz, capacitación o abandonar |
| H4 | Defensa Civil de Malargüe tendrá interés en recibir y actuar sobre las alertas | No validado | Reunión institucional con Defensa Civil (Etapa 0) | El sistema solo sirve para avisar a la escuela, no a emergencias |
| H5 | La frecuencia 915 MHz (o la elegida) es legal para uso escolar sin licencia de radioaficionado | No validado | Consulta a ENACOM o radioaficionados locales (Etapa 0) | Cambio de frecuencia o necesidad de gestionar permisos |
| H6 | Un gateway con PC reciclada (i5-3320M, 4 GB) + internet rural en Bardas Blancas es viable técnicamente | Parcialmente validado | Prueba de estrés del gateway con carga simulada (Etapa 4) | Gateway necesita hardware más potente o mejor conexión |
| H7 | El servidor escolar San José puede recibir y procesar alertas LoRa de forma confiable | Validado parcialmente (infraestructura base existe) | Prueba de integración gateway-servidor (Etapa 4) | El servidor necesita mejoras de red o cómputo |
| H8 | Las instituciones (Gendarmería, Aeropuerto, Municipalidad) aceptarán participar en un protocolo de emergencia | No validado | Conversaciones institucionales formales (Etapa 0-1) | El protocolo opera solo con actores dispuestos |
| H9 | Existen al menos 2-3 puntos en la zona con internet + energía para instalar gateways redundantes | No validado | Relevamiento de infraestructura existente (Etapa 0) | Reducción de redundancia, mayor vulnerabilidad |
| H10 | Una empresa local (minera, petrolera, turística) estará dispuesta a financiar equipos o mantenimiento | No validado | Contacto con empresas identificadas (Etapa 1-2) | Financiamiento completamente autogestionado por la escuela |

> **Nota:** Si H1 o H3 resultan falsas, el proyecto debe detenerse y rediseñarse
> antes de continuar. Son hipótesis existenciales.

---

# 6. Arquitectura del Sistema por Capas

El proyecto no es una "red LoRa". Es un sistema con múltiples capas que deben
diseñarse y operar de forma coordinada. Esta arquitectura por capas permite
entender las dependencias, los riesgos específicos de cada capa y los equipos
necesarios para cada una.

```
┌──────────────────────────────────────────────────────────┐
│  CAPA INSTITUCIONAL                                       │
│  (Colegio, Municipalidad, Defensa Civil, Gendarmería)    │
├──────────────────────────────────────────────────────────┤
│  CAPA HUMANA                                              │
│  (Puesteros, crianceros, usuarios rurales)               │
├──────────────────────────────────────────────────────────┤
│  CAPA OPERATIVA                                           │
│  (Protocolos, alertas, respuesta, escalamiento)          │
├──────────────────────────────────────────────────────────┤
│  CAPA DE DATOS Y VISUALIZACIÓN                            │
│  (InfluxDB, Grafana, dashboards, mapas)                  │
├──────────────────────────────────────────────────────────┤
│  CAPA DE PROCESAMIENTO Y LÓGICA                           │
│  (Servidor San José, Node-RED, MQTT, reglas de alerta)   │
├──────────────────────────────────────────────────────────┤
│  CAPA DE TRANSPORTE Y CONECTIVIDAD                        │
│  (Gateways, Tailscale, internet rural, VPN mesh)         │
├──────────────────────────────────────────────────────────┤
│  CAPA DE RED MESH LORA                                    │
│  (Nodos móviles, repetidores solares, firmware LoRa)     │
├──────────────────────────────────────────────────────────┤
│  CAPA ENERGÉTICA                                          │
│  (Paneles solares, baterías LiFePO4, UPS, power banks)   │
├──────────────────────────────────────────────────────────┤
│  CAPA FÍSICA / INFRAESTRUCTURA                            │
│  (Cajas IP67, mástiles, soportes, anclajes, cableado)    │
├──────────────────────────────────────────────────────────┤
│  CAPA TERRITORIAL                                         │
│  (Relieve, clima, rutas, distancias, zonas de riesgo)    │
├──────────────────────────────────────────────────────────┤
│  CAPA CIENTÍFICA (futuro)                                 │
│  (Datos climáticos, telemetría, predicción meteorológica)│
├──────────────────────────────────────────────────────────┤
│  CAPA EDUCATIVA                                           │
│  (Estudiantes, docentes, formación técnica, currícula)   │
└──────────────────────────────────────────────────────────┘
```

## 6.1 Descripción de cada capa

| Capa | Descripción | Responsable principal |
|------|-------------|----------------------|
| **Institucional** | Relaciones con municipio, Defensa Civil, Gendarmería, empresas. Acuerdos, convenios, actas. | Dirección Colegio + Paulo Alvarez |
| **Humana** | Usuarios finales (puesteros). Capacitación, adopción, retroalimentación. Ciclo anual del puestero. | Docente referente + líder comunitario |
| **Operativa** | Protocolo de emergencia: ¿quién recibe la alerta? ¿qué hace? ¿cuánto tarda? ¿cómo escala? | Definir con Defensa Civil |
| **Datos y visualización** | Dashboards, mapas de cobertura, telemetría histórica, alertas. | Equipo de software estudiantil |
| **Procesamiento y lógica** | Reglas de alerta, integración con APIs, lógica de reenvío, persistencia. | Servidor San José + Node-RED |
| **Transporte** | Gateways, VPN Tailscale, conexión a internet, MQTT bridge. | Equipo técnico + Paulo Alvarez |
| **Red mesh LoRa** | Firmware Meshtastic, configuración de canales, antenas, frecuencias. | Equipo técnico |
| **Energética** | Dimensionamiento solar, baterías, UPS, consumo de nodos. | Equipo de hardware estudiantil |
| **Física** | Cajas estancas, mástiles, protecciones contra clima, animales, vandalismo. | Equipo de hardware estudiantil |
| **Territorial** | Mapas de cobertura RF, DEM, puntos de instalación, logística de campo. | Equipo GIS estudiantil |
| **Científica (futuro)** | Recolección de datos meteorológicos, correlación con alertas, predicción. | Expansión futura |
| **Educativa** | Formación técnica de estudiantes, integración curricular, transferencia entre cohortes. | Docente referente |

---

# 7. Componentes Técnicos

## 7.1 Red LoRa / Meshtastic

### Firmware y frecuencia

- **Firmware base:** Meshtastic (versión a fijar al comprar hardware).
- **Frecuencia:** A definir según regulación ENACOM. Opciones: 433 MHz (mejor
  penetración, antenas más grandes) o 915 MHz (más ancho de banda, antenas más
  pequeñas, común en América).
- **Modulación:** LoRa (CSS — Chirp Spread Spectrum).
- **Potencia de transmisión:** 20-22 dBm (100-150 mW) típico en ESP32 + módulo
  LoRa.

### Hardware considerado

| Componente | Función | Costo estimado (USD) |
|------------|---------|---------------------|
| ESP32 + LoRa (T-Beam, T-Echo, o similar) | Nodo móvil / repetidor | 25-40 |
| Antena 1/4 onda o dipolo para frecuencia elegida | Radiación RF | 5-15 |
| Batería 18650 (3.000-3.500 mAh) | Alimentación nodo móvil | 5-10 |
| Batería LiFePO4 10-20 Ah | Alimentación repetidor fijo | 30-60 |
| Panel solar 10-20W | Carga repetidor | 20-40 |
| Caja estanca IP67 | Protección ambiental | 10-25 |
| Cable USB-C blindado | Conexión y carga | 3-8 |

> **Preguntas abiertas sobre hardware:**
>
> ¿T-Beam PRO (con mejor GPS) vs T-Echo (más económico) vs alternativa
> (Lilygo, Heltec)? ¿Cuál es la mejor relación costo-beneficio para el uso
> específico del puestero?
>
> ¿El módulo GPS de los T-Beam comerciales tiene sensibilidad suficiente en
> cañones de montaña?
>
> ¿Hay disponibilidad real de estos componentes en Argentina con precios
> razonables? ¿O hay que importar?

### Nodos en la red

| Tipo de nodo | Función | Batería | GPS | Cantidad estimada inicial |
|-------------|---------|---------|-----|--------------------------|
| **Nodo móvil (puestero)** | Comunicación personal del puestero. Botón de alerta + posición GPS + mensajes de texto. | 18650 + opcional power bank externo | Sí | 3-5 |
| **Repetidor fijo solar** | Extiende cobertura. Instalado en punto elevado. Sin GPS. | LiFePO4 10-20 Ah + panel solar 10-20W | No | 1-3 |
| **Gateway Bardas Blancas** | Puente entre red LoRa e internet. Conectado a PC reciclada. | UPS + red eléctrica | No | 1 |
| **Gateway redundante (otra ubicación)** | Segundo punto de recepción de alertas. | UPS + red eléctrica | No | 1-2 |

## 7.2 Gateways

### Gateway primario: Bardas Blancas

| Componente | Función | Especificación |
|------------|---------|----------------|
| PC reciclada | Servidor del gateway | i5-3320M, 4 GB RAM, 120 GB SSD |
| SO | Base del sistema | Debian 12 (Bookworm) — LTS hasta 2028 |
| Docker + Compose | Contenedorización | Facilita deployment, actualizaciones, rollback |
| Meshtastic Python API | Interfaz nodo-gateway | Recibe mensajes del nodo LoRa por USB |
| Mosquitto (MQTT) | Bus de mensajes local | Desacopla recepción LoRa de procesamiento |
| Node-RED | Lógica de flujos | Alertas, transformaciones, reenvío |
| InfluxDB | TSDB local | Almacena telemetría si internet cae |
| Grafana (opcional local) | Visualización local | Dashboard en LAN de Bardas Blancas |

### Gateways redundantes

La arquitectura prevé **2-3 gateways** en la zona para garantizar continuidad
operativa ante cortes de luz, fallos de internet o daños de hardware. Cada gateway
debe:

- Estar en una ubicación física diferente.
- Tener conexión a internet propia (no compartir el mismo ISP).
- Tener UPS con autonomía mínima de 30 minutos.
- Poder operar en modo offline acumulando datos hasta que internet regrese.

> **Preguntas abiertas sobre gateways:**
>
> ¿En qué ubicaciones físicas concretas se instalarían los gateways redundantes?
> ¿Las Loicas? ¿Alguna escuela rural? ¿Puesto con internet?
>
> ¿Quién administra cada gateway? Un gateway necesita una persona local que
> pueda reiniciarlo si se cae.
>
> ¿Qué anchos de banda de internet están disponibles en esas ubicaciones? ¿Son
> suficientes para MQTT + telemetría?

## 7.3 Servidores escolares como repetidores de alerta

En situaciones críticas (corte total de internet en Bardas Blancas, falla del
gateway primario), los servidores escolares de la red existente (San José, DS3,
otros establecimientos que se sumen) pueden actuar como **repetidores de alerta**
si están conectados a un nodo LoRa.

El modelo operativo sería:

1. Un nodo LoRa conectado a un servidor escolar recibe una alerta.
2. El servidor la procesa y la reenvía simultáneamente a múltiples destinos:
   - Email a contactos de emergencia.
   - Mensaje a grupo de Telegram/WhatsApp.
   - Otro servidor escolar vía VPN (Tailscale).
   - API a sistema de monitoreo.
3. Si varios servidores reciben la misma alerta, el sistema debe evitar duplicados.

> **Importante:** Los servidores escolares existentes tienen capacidades limitadas.
> No se debe comprometer su funcionamiento principal. Un nodo LoRa conectado a un
> servidor escolar debe ser un **punto de escucha pasivo** que no afecte los
> servicios existentes.

> **Preguntas abiertas sobre servidores como repetidores:**
>
> ¿Qué servidores escolares tienen disponibilidad técnica para sumarse como
> puntos de escucha? ¿Qué establecimientos están interesados?
>
> ¿Cuál es el protocolo de seguridad para conectar un dispositivo LoRa a un
> servidor escolar sin comprometer su seguridad?
>
> ¿Cómo se evitan alertas duplicadas si múltiples servidores reciben el mismo
> mensaje?

## 7.4 Energía para nodos fijos y repetidores

Ver sección específica [Diseño Energético del Nodo del Puestero](#8-diseño-energético-del-nodo-del-puestero)
para nodos móviles.

Para repetidores fijos solares:

| Componente | Especificación | Justificación |
|-----------|----------------|---------------|
| Panel solar | 10-20W monocristalino | Suficiente para carga en días de sol parcial en Malargüe |
| Batería | LiFePO4 10-20 Ah | Segura, 2000+ ciclos, mejor rendimiento en frío que Li-Ion |
| Regulador | MPPT con protección LiFePO4 | Carga eficiente, protege contra sobrecarga y descarga profunda |
| Consumo nodo (deep sleep) | < 1 mA promedio | Wake-up cada 5 min para escucha |
| Autonomía sin sol | 7-10 días estimados | Con batería 10 Ah y consumo promedio 1 mA |
| Carcasa | IP67 mínimo + ventilación térmica | Protección contra polvo, agua y sobrecalentamiento |

### UPS para gateways y servidores

- Gateway Bardas Blancas: UPS de 600-1000 VA. Autonomía estimada: 30-60 min.
- Servidores escolares: UPS existente (verificar estado y capacidad).
- Repetidores solares: No necesitan UPS (ya tienen batería + panel).

---

# 8. Diseño Energético del Nodo del Puestero

## 8.1 Perfil de uso y autonomía requerida

El diseño energético del nodo que lleva el puestero depende directamente del
**ciclo real de actividad en la montaña**, que aún no está completamente definido
(ver [2.2](#22-el-ciclo-anual-del-puestero)). A continuación se presentan los
escenarios posibles y sus implicancias.

### Consumo estimado del nodo móvil

| Modo de operación | Consumo | Tiempo típico por ciclo |
|-------------------|---------|------------------------|
| Deep sleep | < 1 mA | 90% del tiempo (escuchando cada 5-30 min) |
| Receptor pasivo | ~20-30 mA | 10% del tiempo (intervalos de escucha) |
| Transmisión activa | ~100-150 mA | 1-2 segundos por mensaje |
| GPS activo | ~50-80 mA extra | 30-60 segundos por fix |
| **Promedio estimado (modo ahorro)** | **~2-5 mA** | GPS cada 30 min, transmisión cada 1-2 horas |

### Autonomía por configuración

| Configuración | Batería | Autonomía estimada | Ideal para |
|--------------|---------|-------------------|------------|
| Solo 18650 interna (3.000 mAh) | Interna | 3-5 días en modo ahorro | Salidas cortas (fin de semana) |
| 18650 + power bank 5.000 mAh | Total 8.000 mAh | 10-15 días | Salidas de 1-2 semanas |
| 18650 + power bank 10.000 mAh | Total 13.000 mAh | 20-30 días | Temporada completa sin recarga |
| 18650 + panel solar 5W plegable | Recarga diurna | Ilimitado (con sol) | Cualquier duración |

## 8.2 Opciones de energía portátil

### Opción A: Panel solar portátil (5W plegable)

- **Costo:** ~USD 15-25.
- **Ventaja:** Autonomía ilimitada con sol. El puestero lo lleva en la mochila
  o enganchado a la montura.
- **Desventaja:** Elemento adicional que puede olvidarse, romperse o mojarse.
  Depende de condiciones de sol (días nublados reducen la carga).
- **Recomendación para:** Puesteros que pasan más de 5 días consecutivos en
  la montaña.

### Opción B: Ultra bajo consumo (solo 18650)

- **Configuración:** GPS cada 30-60 minutos, transmisión solo manual o cada
  2-4 horas.
- **Costo:** ~USD 0 (solo la batería incluida).
- **Autonomía estimada:** 5-7 días con batería 18650 sola.
- **Desventaja:** Menor frecuencia de actualización de posición. No ideal para
  emergencia donde la posición debe conocerse rápido.
- **Recomendación para:** Salidas cortas de 2-4 días.

### Opción C: Power bank externo (10.000 mAh)

- **Costo:** ~USD 15-25.
- **Ventaja:** Simple para el usuario (conecta y usa). No depende del sol.
  Funciona de noche y en días nublados.
- **Autonomía estimada:** 20-30 días con consumo bajo.
- **Desventaja:** Peso y volumen adicional. Requiere que el puestero recuerde
  cargar el power bank ANTES de la salida.
- **Recomendación para:** La mayoría de los escenarios. Es la opción más
  robusta y simple.

## 8.3 Recomendación según uso real

> **⚠ Hipótesis:** Se asume que el puestero típico pasa entre 3 y 14 días
> consecutivos en la montaña. Esto DEBE VALIDARSE con entrevistas a puesteros
> reales de Bardas Blancas.

**Recomendación inicial (a validar):**

- **Núcleo del nodo:** Batería 18650 interna (3.000 mAh).
- **Extensión estándar:** Power bank 5.000-10.000 mAh que el puestero lleva
  en la mochila. Se conecta al nodo al salir.
- **Para uso prolongado (>7 días sin bajar):** Panel solar plegable 5W
  adicional.
- **Carga en puesto:** USB-C estándar. El puestero carga todo (nodo + power
  bank) cuando baja o en días de descanso.

### Modos de ahorro configurables por perfil

| Perfil | GPS | Escucha | Transmisión | Autonomía esperada |
|--------|-----|---------|-------------|-------------------|
| Emergencia máxima | Cada 2 min | Continua | Cada 5 min | 1-2 días (solo batería interna) |
| Estándar | Cada 10 min | Cada 30 seg | Cada 30 min | 3-5 días |
| Ahorro | Cada 30 min | Cada 5 min | Manual | 5-7 días |
| Ultra ahorro | Apagado | Cada 10 min | Manual | ~10 días |

> **Preguntas abiertas sobre energía del puestero:**
>
> ¿Cuántos días consecutivos pasa realmente un puestero en la montaña de Bardas
> Blancas sin bajar? Esto es el dato más importante para dimensionar la batería.
>
> ¿Tienen los puesteros acceso a corriente eléctrica en sus puestos base para
> cargar los nodos entre salidas?
>
> ¿Aceptarían los puesteros llevar un power bank adicional en la mochila o
> prefieren un dispositivo único?
>
> ¿Un panel solar plegable se dañaría con el uso rudo de montaña (golpes,
> lluvia, nieve, viento)?

---

# 9. Protocolo de Emergencia y Coordinación Institucional

Esta es probablemente la sección más importante del proyecto después de la
validación técnica. Un sistema técnico que funciona pero no tiene un protocolo
humano de respuesta es un sistema incompleto.

## 9.1 Actores institucionales identificados

| Actor | Rol potencial en el protocolo | Contacto |
|-------|-------------------------------|----------|
| **Municipalidad de Malargüe** | Coordinación civil, recursos de emergencia, logística | Pendiente de establecer |
| **Defensa Civil Malargüe** | Recepción de alertas, respuesta en terreno, protocolo de emergencia | Pendiente de establecer |
| **Gendarmería Nacional (Destacamento Las Loicas)** | Presencia territorial real en zona de veranada. Respuesta inmediata en campo | Pendiente de establecer |
| **Aeropuerto de Malargüe** | Capacidad de evacuación aérea en emergencias graves. Coordinación con protocolo | Pendiente de establecer |
| **Hospital Malargüe** | Recepción de alertas sanitarias, coordinación de evacuación médica | Pendiente de establecer |
| **Colegio San José** | Monitoreo del sistema, primera recepción de alertas, escalamiento | Paulo Alvarez + Dirección |

## 9.2 Modelo operativo: ¿quién recibe la alerta?

Actualmente NO está definido. Es una de las decisiones más urgentes que debe
tomarse en la Etapa 0.

### Posibles modelos de flujo de alerta

```
Modelo A: Escuela como centro de monitoreo
  Puestero → Red LoRa → Gateway → Servidor San José → Escuela monitorea
  Escuela → Llama a Defensa Civil / Gendarmería / Emergencias

Modelo B: Derivación directa a autoridades
  Puestero → Red LoRa → Gateway → Servidor San José → Alerta automática
  a Defensa Civil + Gendarmería + Escuela (todos reciben simultáneamente)

Modelo C: Múltiples puntos de escucha
  Puestero → Red LoRa → Múltiples gateways → Servidores escolares +
  Defensa Civil + Gendarmería reciben en paralelo
```

> **Pregunta crítica:**
>
> ¿Cuál de estos modelos es operable en Malargüe hoy? ¿Defensa Civil tiene
> capacidad de recibir alertas electrónicas (email, Telegram, sistema propio)?
> ¿O todo debe pasar por una llamada telefónica humana?

## 9.3 Protocolo mínimo viable

Hasta que se defina el modelo operativo con las autoridades, se propone un
protocolo mínimo para la fase de pruebas:

1. Las alertas de prueba son recibidas exclusivamente por el equipo del proyecto
   (Paulo Alvarez + docente referente).
2. Durante pruebas, se mide: tiempo desde que el puestero envía hasta que el
   servidor recibe.
3. No se escala a autoridades hasta que el sistema demuestre confiabilidad en
   pruebas controladas (mínimo 50 mensajes con tasa de éxito > 90%).
4. Una vez validado, se presenta el sistema a Defensa Civil con datos concretos.
5. Se diseña el protocolo formal CON Defensa Civil, no antes.

### Preguntas para diseñar el protocolo con autoridades

> **Preguntas abiertas del protocolo:**
>
> ¿Quién recibe la alerta primero?
>
> ¿Cómo se valida que la alerta es real (no una falsa alarma)?
>
> ¿Qué prioridad tiene la alerta? (¿todas las alertas son críticas o hay
> niveles?)
>
> ¿Quién responde? ¿Defensa Civil? ¿Gendarmería? ¿Municipio?
>
> ¿Cuánto tiempo máximo debe pasar desde la alerta hasta la primera acción?
>
> ¿Qué pasa si nadie responde en 30 minutos? ¿60 minutos?
>
> ¿Cómo se cierra el ciclo? ¿Quién confirma que el puestero está a salvo?
>
> ¿Existe algún sistema de emergencias existente en Malargüe con el cual
> este protocolo deba integrarse?

## 9.4 Puntos de escucha redundantes

Se propone que las alertas no dependan de un solo gateway. En la medida de lo
posible, el sistema debe tener **múltiples puntos de escucha** que reciban y
reenvíen la misma alerta de forma independiente.

### Posibles puntos de escucha

| Ubicación | Tipo | Ventaja | Desafío |
|-----------|------|---------|---------|
| Bardas Blancas (gateway primario) | Gateway completo | Cobertura local directa | Depende de internet rural |
| Escuela rural o puesto con internet | Gateway secundario | Redundancia geográfica | Identificar ubicación concreta |
| Gendarmería Las Loicas | Gateway institucional | Presencia permanente, seguridad | Requiere acuerdo institucional |
| Aeropuerto Malargüe | Gateway institucional | Energía + internet confiables | Lejano de zona de veranada |
| Servidor escolar San José | Punto de escucha pasivo | Ya existe, monitoreado | Alcance LoRa puede no llegar |

> **Pregunta abierta:**
>
> ¿Cuántos gateways se necesitan realmente para garantizar redundancia útil?
> ¿2 es suficiente o se necesitan 3?

---

# 10. Redundancia y Resiliencia de Infraestructura

Esta sección documenta las decisiones de diseño orientadas a que el sistema
soporte fallos sin dejar de funcionar.

## 10.1 Escenarios de fallo contemplados

| Escenario | Impacto | Mitigación |
|-----------|---------|------------|
| Corte de luz en Bardas Blancas | Gateway sin energía | UPS (30 min) + modo offline acumulando datos |
| Corte de internet en Bardas Blancas | Gateway no puede reenviar a servidor | Almacenamiento local en InfluxDB. Reenvío cuando internet vuelva. Red LoRa sigue operando localmente. |
| Falla de hardware del gateway | Pérdida del gateway principal | Gateway redundante en otra ubicación |
| Falla del servidor San José | Sin procesamiento central | Gateway opera localmente. Alerta no se pierde (almacenada localmente). |
| Días sin sol en repetidor solar | Repetidor se apaga | Batería dimensionada para 7-10 días sin sol. Telemetría de batería para alerta temprana. |
| Caída de Tailscale / VPN | Sin conexión cifrada entre nodos | Los gateways pueden tener conexión directa a internet como respaldo (con firewall restrictivo). |

## 10.2 Decisiones de diseño para resiliencia

| Decisión | Justificación |
|----------|---------------|
| Múltiples gateways (2-3) en ubicaciones diferentes | Si un gateway falla, otro puede recibir la alerta |
| Gateway opera sin internet | La red LoRa es independiente de internet. Los mensajes se almacenan y reenvían cuando hay conexión. |
| Almacenamiento local en cada gateway | InfluxDB local garantiza que no se pierdan datos aunque el servidor central esté caído |
| Monitoreo proactivo de cada nodo | El servidor debe alertar antes de que algo falle (batería baja, nodo offline >24h, disco lleno) |
| UPS en cada gateway y servidor | Autonomía mínima de 30 minutos para gateway, 15 minutos para servidor escolar |
| Protocolo de reinicio remoto vía Tailscale | Si el gateway se congela, se puede reiniciar remotamente sin ir al lugar |

---

# 11. Gobernanza y Marco Institucional

## 11.1 Propiedad y control

El proyecto pertenece institucionalmente al **Colegio Diocesano San José**.
Ningún estudiante, docente, colaborador externo, empresa o institución puede
apropiarse de la infraestructura, los datos o la propiedad intelectual del
proyecto.

### Cláusula de patrocinio

> Toda colaboración externa —empresarial, institucional o individual— será
> considerada patrocinio o apoyo institucional. Ningún patrocinio implica
> transferencia de propiedad intelectual, acceso exclusivo a la infraestructura
> o los datos, control operativo del proyecto, ni uso comercial de los datos
> generados. La toma de decisiones sobre el rumbo técnico e institucional del
> proyecto es exclusiva del Colegio San José.

## 11.2 Estructura de gobernanza

| Nivel | Actor | Decisiones |
|-------|-------|------------|
| **Estratégico** | Dirección del Colegio San José | Nombre oficial, acta de creación, relaciones institucionales, acuerdos de patrocinio, continuidad del proyecto. |
| **Técnico-educativo** | Docente referente + Capacitador técnico | Arquitectura del sistema, elección de hardware/software, plan de etapas, decisiones de seguridad. |
| **Operativo estudiantil** | Equipo de estudiantes (líder de etapa) | Implementación técnica, mediciones, documentación operativa, mantenimiento diario. |
| **Comunitario (a futuro)** | Representantes de puesteros / municipio | Retroalimentación sobre necesidades reales, adopción, validación de utilidad. |

## 11.3 Política de datos

### Datos recopilados por el sistema

| Dato | Propósito | ¿Sensible? |
|------|-----------|------------|
| Posición GPS del puestero | Saber dónde está en caso de emergencia | Sí. Revela ubicación de personas. |
| Mensajes de texto del puestero | Comunicación de emergencia o coordinación | Sí. Contenido privado. |
| Telemetría climática (temp, humedad, presión) | Monitoreo ambiental, predicción | No. Dato ambiental agregado. |
| Estado de batería del nodo | Mantenimiento preventivo | No. Dato técnico. |
| RSSI/SNR de cada transmisión | Mapa de cobertura RF | No. Dato técnico agregado. |

### Reglas propuestas

| Aspecto | Regla propuesta |
|---------|----------------|
| **Acceso** | Solo personal autorizado del Colegio San José. No se comparte con terceros sin consentimiento expreso. |
| **Retención** | Telemetría: 1 año. Mensajes: 90 días. Posiciones GPS: 90 días (menos si el puestero solicita eliminación). |
| **Protección** | Datos almacenados en servidor San José con acceso solo por Tailscale VPN. No accesibles desde internet sin autenticación. |
| **Derecho del usuario** | Cualquier puestero puede solicitar que sus datos sean eliminados. Debe haber un proceso simple para hacerlo. |

### Relación con DS3 y Pierre Auger

El Observatorio Pierre Auger y la DS3 (ESA/CONAE) son instituciones con
estándares de seguridad extremadamente altos. **No se debe:**

- Pedirles que alojen servicios del proyecto en su infraestructura de producción.
- Conectar dispositivos del proyecto a sus redes internas sin autorización y
  auditoría de seguridad.

**Lo que SÍ es posible y realista:**

- Asesoramiento técnico y de estándares por parte de su personal.
- Validación de arquitectura y buenas prácticas.
- Que el proyecto adopte estándares de seguridad inspirados en los de estas
  instituciones.
- Que una persona del Auger o DS3 esté en la lista de contactos de emergencia
  como punto de escalamiento institucional.
- Donación de hardware en desuso que cumpla con los requisitos del proyecto.
- Participación como mentores o evaluadores externos del proyecto educativo.

> **Pregunta abierta:**
>
> ¿Existe algún contacto directo con personal del Observatorio Pierre Auger o
> de la DS3? Sin un contacto, cualquier conversación institucional es más
> difícil.

---

# 12. Sostenibilidad del Proyecto

## 12.1 Sostenibilidad técnica

- **Documentación como producto primario:** cada componente instalado debe tener
  su ficha técnica, fecha de instalación, número de serie, configuración y notas.
  Un técnico desconocido debe poder retomar el proyecto solo con la documentación.
- **Estándares reproducibles:** todos los servicios en Docker con docker-compose
  documentado. Configuraciones en repositorio Git. Nada debe estar solo en la
  memoria de alguien.
- **Hardware con larga vida útil:** preferir hardware con comunidad activa y
  reemplazos accesibles en Argentina. Mantener stock mínimo de repuestos.
- **Monitoreo proactivo:** el servidor debe alertar antes de que algo falle
  (batería baja, nodo offline, disco lleno).

## 12.2 Sostenibilidad humana

- **Acta institucional formal:** el proyecto pertenece al Colegio San José, no a
  una persona. Debe definir quién toma decisiones cuando el referente actual no
  está (cambio de trabajo, enfermedad, etc.).
- **Transferencia entre cohortes:** protocolo formal de traspaso al inicio de
  cada año escolar. El equipo saliente documenta y entrena al entrante.
- **Red de colaboradores externos:** radioaficionados locales, comunidad
  Meshtastic Argentina, INTA, Defensa Civil. Estas relaciones son reserva de
  conocimiento y recursos.
- **Evitar dependencia de una sola persona:** documentar TODO. Si solo una persona
  sabe cómo funciona el gateway, el proyecto es frágil.

## 12.3 Sostenibilidad financiera

### Modelo de financiamiento

| Fuente | Tipo | Estado |
|--------|------|--------|
| **Fondos propios Colegio San José** | Capital semilla | Disponible para Etapa 1 (~USD 100) |
| **Empresas locales mineras/petroleras** | Sponsorship o donación | No contactadas. Identificar empresas que operan en Malargüe (YPF, Pluspetrol, otras). |
| **Empresas turísticas (Las Leñas, termas)** | Sponsorship | No contactadas. Evaluar pertinencia. |
| **Municipalidad de Malargüe** | Convenio institucional | No contactado. Puede incluir recursos humanos o materiales. |
| **INTA Malargüe** | Colaboración técnica | No contactado. Hardware, asesoramiento, acceso a redes de sensores. |
| **Universidades (UNCUYO/UTN)** | Convenio de extensión | No contactado. Pasantías, tesinas, asesoría técnica. |
| **Donaciones voluntarias / crowdfunding** | Aporte individual | Evaluar si es necesario. Campaña de exalumnos o comunidad. |
| **Mantenimiento profesional financiado por empresa** | Sponsor técnico | Empresa dona horas de su personal técnico o financia a un técnico local. Modelo a explorar. |
| **CONICET / MINCyT** | Subsidio I+D | Proceso largo. Para fases avanzadas, no para Etapa 1. |

### Presupuesto estimado por etapa

| Etapa | Concepto | Costo estimado (USD) |
|-------|----------|---------------------|
| Etapa 0 | Fundamentos (sin hardware) | ~0 (solo tiempo) |
| Etapa 1 | 2 nodos LoRa + antenas + baterías | 80-150 |
| Etapa 2 | Mapeo urbano (sin costo adicional) | ~0 |
| Etapa 3 | Pruebas rurales (combustible + viáticos) | 50-100 |
| Etapa 4 | Gateway Bardas Blancas (PC reciclada + UPS) | 50-150 (si no hay PC disponible) |
| Etapa 5 | 1-2 repetidores solares | 100-200 cada uno |
| Etapa 6 | Sensores climáticos | 30-80 |
| **Total estimado fases 1-6** | | **~USD 400-900** |

> **Preguntas abiertas sobre financiamiento:**
>
> ¿Existe alguna empresa específica en Malargüe que ya haya mostrado disposición
> a colaborar con proyectos educativos o comunitarios?
>
> ¿El Colegio San José tiene experiencia en convenios de sponsor con empresas
> locales?
>
> ¿Se puede involucrar a la comunidad de exalumnos como donantes del proyecto?
>
> ¿El mantenimiento profesional financiado implica contratar a alguien o que
> una empresa done horas de su personal técnico?

---

# 13. Modelo Educativo y Participación Estudiantil

## 13.1 Áreas de formación técnica

| Área | Contenidos concretos | Etapas vinculadas |
|------|---------------------|-------------------|
| Telecomunicaciones RF | LoRa, propagación, antenas, RSSI/SNR, simulación cobertura | 1, 2, 3, 5 |
| Electrónica aplicada | ESP32, sensores I2C/SPI, soldadura, protección ambiental | 1, 6 |
| Sistemas operativos | Linux/Debian, CLI, Docker, servicios, logs | 4, servidor |
| Redes | TCP/IP, MQTT, Tailscale VPN, firewalls | 4, servidor |
| Programación | Python, MicroPython, Node-RED, APIs REST, Bash | 4, 6, 7 |
| Energía renovable | Sistemas fotovoltaicos, LiFePO4, MPPT, cálculo autonomía | 5 |
| GIS y cartografía | GPS, QGIS, georreferenciación, mapas de cobertura RF | 2, 3, 7 |
| Gestión de datos | InfluxDB, Grafana, series temporales, dashboards | 7 |
| Gestión de proyectos | Documentación técnica, GitHub, Kanban, revisiones de etapa | Todas |

## 13.2 División de roles sugerida

| Rol | Perfil | Responsabilidades |
|-----|--------|-------------------|
| Líder técnico de etapa | Estudiante avanzado (5to/6to año) | Coordina tareas técnicas de la etapa. Documenta. |
| Equipo de campo | Estudiantes con disponibilidad para salidas | Mediciones de cobertura, instalación, relevamiento. |
| Equipo de software | Estudiantes con orientación programación | Scripts Python, Node-RED, dashboards, APIs. |
| Equipo de hardware | Estudiantes con orientación electrónica | Ensamblaje de nodos, antenas, cajas estancas, energía. |
| Documentalista | Estudiante con habilidades de escritura técnica | Mantiene el repositorio, informes, registro de pruebas. |
| Docente referente | Docente de informática/electrónica | Supervisa, conecta el proyecto al currículo, gestiona relaciones. |
| Capacitador técnico | Paulo Alvarez (u otro externo) | Asesoría técnica, revisión de arquitectura, documentación maestra. |

## 13.3 Integración curricular

Para que el proyecto sea sustentable a largo plazo, debe integrarse formalmente
al plan de estudios:

- Incluir Red Cóndor como proyecto integrador de los últimos dos años de la
  orientación informática.
- Asignar horas de espacio curricular específico para el proyecto (mínimo 2 hs
  semanales).
- Incluir el proyecto en la propuesta pedagógica institucional (PEI).
- Vincular con la práctica profesionalizante si la orientación lo permite.
- Transferencia formal entre cohortes: protocolo al inicio de cada año escolar.

> **Preguntas abiertas educativas:**
>
> ¿El plan de estudios actual de la orientación informática permite integrar
> este proyecto como proyecto integrador formal?
>
> ¿Cuántos estudiantes por año tienen el perfil técnico para contribuir
> significativamente al proyecto?
>
> ¿Los docentes involucrados tienen formación en telecomunicaciones y redes
> suficiente o requieren capacitación?

---

# 14. Estrategia de Documentación y Repositorio

## 14.1 Estructura de repositorio propuesta

```
red-condor/
├── README.md                   # Estado actual, descripción, cómo contribuir
├── docs/
│   ├── contexto/               # Este documento y versiones anteriores
│   ├── etapas/                 # Informes de cada etapa: metodología, resultados, métricas
│   ├── hardware/               # Fichas técnicas de cada nodo (modelo, SN, fecha, ubicación)
│   ├── servidor/               # Configuración, servicios, backups, incidentes
│   ├── protocolos/             # Instalación, medición, mantenimiento, emergencia
│   └── decisiones/             # Registro de decisiones técnicas e institucionales
├── firmware/                   # Versiones de firmware y configuraciones (.toml)
├── software/                   # Scripts Python, flows Node-RED, docker-compose
├── mapas/                      # Archivos GIS, mapas de cobertura RF, tracks GPS
├── fotos/                      # Instalaciones, pruebas de campo, eventos educativos
└── protocolos/                 # Procedimientos operativos
```

## 14.2 Protocolo de documentación de pruebas

Cada prueba de campo debe registrar como mínimo:

- Fecha, hora y condiciones climáticas.
- Firmware Meshtastic versión, configuración de canal y frecuencia.
- Hardware usado: modelo de nodo, antena, batería.
- Ubicación de cada nodo (coordenadas GPS).
- Métricas: RSSI, SNR, paquetes enviados vs. recibidos, latencia.
- Incidentes: fallos, comportamientos inesperados, observaciones.
- Conclusiones: ¿qué se aprendió? ¿qué se cambia para la próxima?
- Registro fotográfico.

> **Preguntas abiertas:**
>
> ¿El Colegio tiene cuenta institucional en GitHub o se usará una cuenta personal?
>
> ¿Los estudiantes tienen formación básica en Git?
>
> ¿Existe un sistema de gestión de tareas (Trello, Notion, GitHub Projects)
> en uso en la institución?

---

# 15. Plan de Implementación por Etapas

Filosofía: **No se avanza a la siguiente etapa hasta que la anterior esté
validada, documentada y con métricas registradas.**

| Etapa | Objetivo | Entregables | Métricas de éxito | Duración est. |
|-------|----------|-------------|-------------------|---------------|
| **0 — Fundamentos** | Marco institucional, simulación RF, repositorio | Acta institucional, DEM analizado, repo creado | Acta firmada, puntos candidatos identificados | 2-4 semanas |
| **1 — Prueba de concepto** | 2 nodos funcionando con Meshtastic | 2 nodos configurados, primera medición de alcance | Mensajes entregados a >500m. RSSI y SNR registrados. | 2-4 semanas |
| **2 — Mapeo urbano** | Caracterizar RF en Malargüe | Mapa de cobertura Malargüe urbano | Cobertura >80% del ejido urbano documentada | 2-3 semanas |
| **3 — Pruebas rurales** | Cobertura en corredor Bardas Blancas | Mapa RF corredor, puntos repetidores validados | Alcance real medido en ≥3 puntos del corredor | 2-4 semanas |
| **4 — Gateway Bardas Blancas** | Conectar red LoRa al servidor San José | Gateway operativo, datos en InfluxDB | 1 mensaje recibido en servidor San José desde campo | 3-4 semanas |
| **5 — Repetidores solares** | Extender cobertura con nodos autónomos | ≥1 repetidor solar instalado | Operativo >30 días sin intervención | 4-8 semanas |
| **6 — Sensores climáticos** | Telemetría ambiental | Datos de T°, humedad, presión en dashboard | Actualización correcta en dashboard cada N minutos | 4-6 semanas |
| **7 — Plataforma avanzada** | Alertas automáticas y mapas públicos | Dashboard público, alertas por email operativas | Alerta generada en <30 seg de evento umbral | 8-12 semanas |

## 15.1 Etapa 0: Fundamentos (inmediata — sin comprar hardware)

- [ ] Redactar y firmar el Acta de Creación del Proyecto Red Cóndor.
- [ ] Crear repositorio GitHub institucional con estructura propuesta.
- [ ] Entrevistar a puesteros o contactos rurales para definir ciclo anual real
      (ver [2.2](#22-el-ciclo-anual-del-puestero)).
- [ ] Descargar DEM de Malargüe y realizar simulación RF del corredor Bardas
      Blancas (Radio Mobile o SPLAT!).
- [ ] Consultar a ENACOM o radioaficionados sobre la frecuencia de operación.
- [ ] Contactar al club de radioaficionados de Malargüe/Mendoza.
- [ ] Conectar servidor San José al switch por Ethernet.
- [ ] Instalar InfluxDB + Grafana + Mosquitto en servidor San José (Docker).

> **Preguntas abiertas de la Etapa 0:**
>
> ¿El calendario escolar tiene recesos que obliguen a pausar etapas?
>
> ¿Las pruebas en Bardas Blancas requieren autorización municipal o de
> propietarios?
>
> ¿Los estudiantes pueden participar en salidas de campo en horario escolar?

---

# 16. Plan de Expansión Territorial

## 16.1 Corredor primario: Bardas Blancas

El punto de partida. Objetivo de la Fase 1 es caracterizar RF, instalar gateway
y probar con 2-3 puesteros reales.

## 16.2 Corredores secundarios (priorizados)

| Orden | Corredor | Justificación | Requisitos para expansión |
|-------|----------|---------------|---------------------------|
| 1 | **Bardas Blancas → Las Loicas** | Presencia de Gendarmería y Aduana. Infraestructura existente. | Gateway validado en Bardas Blancas. Acuerdo con Gendarmería. |
| 2 | **Real del Pehuenche** | Paso internacional. Tránsito estacional. Conectividad con Las Loicas. | Repetidores solares intermedios. |
| 3 | **Cajón Grande** | Zona de veranada continua con Bardas Blancas. | Repetidores adicionales. |
| 4 | **Valle Hermoso / Los Molles** | Turismo termal. Población dispersa. Potencial económico. | Evaluar demanda real. |
| 5 | **Las Leñas** | Perfil diferente (turismo de nieve, no emergencia rural). | Evaluar pertinencia. No es prioridad inicial. |

## 16.3 Criterios para decidir expansión

- ¿Hay demanda real de la comunidad de esa zona?
- ¿Existe infraestructura (energía, internet, edificio seguro) para gateway?
- ¿La cobertura LoRa desde el corredor activo llega naturalmente?
- ¿Hay un referente local que pueda ser custodio del nodo/gateway?
- El proyecto no debe expandirse hasta que el corredor anterior esté operativo
  y documentado por al menos 3 meses.

---

# 17. Análisis de Riesgos

## 17.1 Matriz de riesgos

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|-------------|---------|------------|
| Alcance LoRa insuficiente en cañones | Alta | Alto | Simulación RF previa. Planificar más repetidores. Validar antes de comprometerse. |
| Falla del gateway Bardas Blancas | Media | Alto | Almacenamiento local robusto. Monitoreo remoto. Capacitar local. Gateway redundante. |
| Corte de internet en Bardas Blancas | Alta | Medio | Red LoRa sigue operando. Gateway acumula datos. Operación sin internet como modo normal. |
| Corte de luz prolongado en Bardas Blancas | Alta | Medio | UPS (30 min). Gateway en modo offline. |
| Fallo energético en repetidor remoto (días sin sol) | Media | Alto | Batería para 7-10 días. Telemetría de batería. Visitas de mantenimiento. |
| No adopción por usuarios rurales | Media | Muy alto | Diseño centrado en usuario. Capacitación repetida. Demostración real. Embajador comunitario. |
| Cambio de firmware Meshtastic rompe compatibilidad | Media | Medio | Fijar versión. Documentar versión de cada nodo. Probar actualización antes de aplicar. |
| Pérdida de continuidad al graduarse estudiantes | Alta | Alto | Documentación rigurosa. Transferencia formal entre cohortes. Acta institucional. |
| Regulación ENACOM bloquea frecuencia | Baja | Alto | Investigar antes de distribuir. Contactar radioaficionados. |
| Robo o vandalismo de nodos remotos | Media | Medio | Instalación discreta. Registro de nodos. Comunidad como custodios. |
| Dependencia de una sola persona (Paulo Alvarez) | Alta | Muy alto | Documentación exhaustiva. Capacitación de reemplazo. Acta institucional. Transferencia de conocimiento. |
| Puestero no lleva el nodo a la montaña | Media | Muy alto | Diseño integrado a su equipo habitual. Capacitación. Validación con prueba real. |
| Falsa sensación de seguridad en usuarios | Media | Alto | Comunicación clara de limitaciones. "Lo que NO es el proyecto" (Sección 4). |

## 17.2 Riesgos específicos de la etapa actual

| Riesgo | Descripción |
|--------|-------------|
| **Sobre-expansión conceptual** | El proyecto tiene muchas ramas (LoRa, Meshtastic, APRS, GIS, IA, sensores, dashboards). Riesgo de dispersarse. Mitigación: objetivo operativo de fase 1 muy simple. |
| **Validación RF pendiente** | No se sabe si LoRa funciona en el terreno real. Ningún mapa, simulación o teoría reemplaza una prueba con dos nodos en Bardas Blancas. |
| **Ciclo del puestero no validado** | El diseño energético depende de saber cuánto tiempo pasa el puestero en la montaña. Si eso no se sabe con precisión, el diseño es especulativo. |
| **Protocolo de emergencia inexistente** | Las alertas no tienen destino claro. Sin Defensa Civil o Gendarmería involucrados, el sistema alerta pero nadie responde. |
| **Presupuesto no comprometido** | No hay dinero comprado, no hay hardware. Hasta que se compren los primeros nodos, el proyecto es solo documentación. |

---

# 18. Métricas de Validación y Telemetría

## 18.1 Métricas de radio frecuencia

| Métrica | Descripción | Valor referencia | Cómo medir |
|---------|-------------|------------------|------------|
| RSSI | Potencia de señal recibida (dBm) | Aceptable: -70 a -120 dBm | App Meshtastic o log del firmware |
| SNR | Señal/Ruido (dB) | Bueno: >5 dB. Límite: >-10 dB | App Meshtastic o log del firmware |
| PER (Packet Error Rate) | % de paquetes perdidos | Objetivo: <10% en condiciones normales | Contador firmware / Node-RED |
| Latencia de mensaje | Tiempo transmisión → recepción | Objetivo: <10 seg en red de 3 saltos | Timestamp origen y destino |
| Alcance con RSSI > -110 dBm | Distancia máxima con señal aceptable | Validar en campo real | Recorridos GPS + log RSSI |

## 18.2 Métricas de sistema y nodo

| Métrica | Descripción | Cómo monitorear |
|---------|-------------|-----------------|
| Voltaje de batería | Estado energético del nodo | Telemetría Meshtastic (campo battery_level) |
| Uptime del nodo | Tiempo sin reinicios | Log de Meshtastic / MQTT |
| Temperatura interna | Alerta de sobrecalentamiento | Sensor DS18B20 opcional |
| Satélites GPS | Calidad del fix GPS | Campo gps_satellites en telemetría |
| Disponibilidad gateway | % tiempo online del gateway | Ping desde servidor San José vía Tailscale |
| Mensajes/día | Volumen de tráfico en la red | Contador en Node-RED / InfluxDB |

---

# 19. Integración con Radioafición y APRS

LoRa/Meshtastic no resuelve todos los escenarios. La comunicación de voz en
tiempo real (crítica en emergencias médicas complejas) requiere radioafición
VHF/UHF.

| Sistema | Capacidad | Limitación | Rol en Red Cóndor |
|---------|-----------|------------|-------------------|
| LoRa/Meshtastic | Texto, GPS, telemetría. Sin internet. Largo alcance. | Sin voz. Latencia. Sin garantía de entrega. | Capa primaria de comunicación rural. |
| VHF radioafición | Voz en tiempo real. Bien establecido. | Requiere licencia. Alcance limitado sin repetidor. | Capa de voz complementaria para emergencias. |
| APRS | GPS, telemetría, mensajes texto. Red global. | Requiere licencia. Infraestructura preexistente. | Redundancia y extensión de alcance global. |
| Satelital (Garmin/Iridium) | Global. Sin dependencia local. | Costo alto. Suscripción. | Respaldo institucional. No para usuarios rurales. |

> **Preguntas abiertas:**
>
> ¿Existe infraestructura APRS activa en Mendoza con cobertura en Malargüe?
>
> ¿Algún docente o colaborador tiene licencia de radioaficionado para operar
> VHF/APRS legalmente?

---

# 20. Antecedentes, Alianzas e Instituciones Relacionadas

## 20.1 Observatorio Pierre Auger

El Observatorio Pierre Auger opera más de 1600 detectores distribuidos en
3.000 km² de campo patagónico. Su infraestructura comparte características
directas con Red Cóndor: nodos remotos autónomos con energía solar, telemetría
distribuida, comunicaciones resilientes. Representa el aliado institucional
más valioso potencial: prestigio científico, experiencia técnica, presencia
local y disposición a actividades educativas.

**Rol potencial:** Asesoramiento técnico, estándares de seguridad, contacto
institucional de escalamiento, donación de hardware educativo.

## 20.2 DS3 Malargüe (ESA/CONAE)

La antena de espacio profundo confirma a Malargüe como nodo tecnológico de
relevancia internacional. Es un argumento de contexto valioso para comunicación
institucional.

**Rol potencial:** Estándares de seguridad, asesoramiento, punto de escucha
pasivo (evaluar).

## 20.3 INTA Malargüe

Interés natural en monitoreo climático y agropecuario. La red de sensores
climáticos de Red Cóndor puede ser de interés directo para INTA en etapas
avanzadas.

**Rol potencial:** Convenio de colaboración técnica, acceso a redes de
sensores existentes, asesoramiento agronómico.

## 20.4 Comunidad Meshtastic Argentina

Comunidad activa (Buenos Aires, Córdoba, Mendoza). Puede proveer experiencia
práctica, conocimiento de regulación, hardware disponible, colaboradores
técnicos remotos.

## 20.5 Radioaficionados de Malargüe y Mendoza

Aliados naturales: conocen el territorio, tienen experiencia en propagación RF
local, pueden aportar equipos VHF y experiencia APRS.

---

# 21. Registro de Decisiones Abiertas

## 21.1 Decisiones técnicas críticas

| Decisión | Por qué es crítica | Responsable | Estado |
|----------|-------------------|-------------|--------|
| Frecuencia de operación (433 vs 915 MHz) | Define hardware a comprar y legalidad | Paulo Alvarez + radioaficionado | Pendiente |
| Hardware nodo móvil (T-Beam vs alternativas) | Define costo, disponibilidad, capacidades del MVP | Paulo Alvarez | Pendiente |
| Versión firmware Meshtastic a fijar | Evita incompatibilidades | Equipo técnico | Pendiente (al comprar) |
| Arquitectura de antenas repetidores | Omnidireccional vs directiva | Post simulación RF | Pendiente |
| Cantidad mínima de repetidores para corredor BB | Define inversión inicial | Post pruebas campo | Pendiente |
| Modelo de flujo de alerta (A, B o C) | Define quién recibe y cómo | Con Defensa Civil | Pendiente |
| Ubicación de gateways redundantes | Define resiliencia | Equipo técnico | Pendiente |

## 21.2 Decisiones institucionales

| Decisión | Responsable | Estado |
|----------|-------------|--------|
| Nombre oficial del proyecto | Dirección San José | 🟡 En proceso |
| Redacción y firma del Acta de Creación | Dirección + Paulo Alvarez | ❌ Pendiente |
| Integración curricular formal | Dirección + Docente referente | ❌ Pendiente |
| Política de privacidad y datos de usuarios | Dirección San José | ❌ Pendiente |
| Identificación de docente referente | Dirección San José | 🟡 En proceso |
| Contacto con Defensa Civil Malargüe | Paulo Alvarez + Dirección | ❌ Pendiente |
| Contacto con Gendarmería Las Loicas | Paulo Alvarez + Dirección | ❌ Pendiente |

## 21.3 Decisiones de financiamiento

| Decisión | Monto estimado | Responsable | Estado |
|----------|---------------|-------------|--------|
| Compra 2 nodos LoRa (Etapa 1) | USD 80-120 | Dirección San José | ❌ Pendiente |
| Identificar primer patrocinador | Variable | Paulo Alvarez + Dirección | ❌ Pendiente |
| Presupuesto anual del proyecto | A definir | Dirección San José | ❌ Pendiente |

---

# 22. Hoja de Ruta y Próximas Acciones

## 22.1 Próximos 30 días (Etapa 0)

- [ ] **Prioridad 1:** Entrevistar a puesteros o contactos rurales para definir
      el ciclo anual real de actividad en la montaña. Sin este dato, el diseño
      energético es especulativo.
- [ ] Redactar y firmar el Acta de Creación del Proyecto Red Cóndor.
- [ ] Crear repositorio GitHub institucional.
- [ ] Consultar a ENACOM o radioaficionados sobre frecuencia legal.
- [ ] Descargar DEM de Malargüe y primera simulación RF del corredor Bardas Blancas.
- [ ] Conectar físicamente el servidor San José a Ethernet.
- [ ] Instalar InfluxDB + Grafana + Mosquitto en servidor San José (Docker).
- [ ] Contactar radioaficionados de Malargüe/Mendoza.

## 22.2 Próximos 60-90 días (Etapas 1 y 2)

- [ ] Compra de 2 nodos LoRa (confirmar modelo y proveedor en Argentina).
- [ ] Instalación de Meshtastic y primera configuración de red.
- [ ] Pruebas de alcance en Malargüe urbano con registro de métricas.
- [ ] Primer mapa de cobertura RF de Malargüe.
- [ ] Primera salida a Bardas Blancas: prueba de cobertura en corredor real.
- [ ] Inicio de configuración del gateway en PC reciclada.

## 22.3 Próximos 6 meses

- [ ] Gateway Bardas Blancas operativo y conectado al servidor San José.
- [ ] Primer repetidor solar instalado.
- [ ] Primer dashboard público con telemetría básica.
- [ ] Presentación del sistema a Defensa Civil con datos de pruebas.
- [ ] Inicio de diseño del protocolo de emergencia.

---

# Apéndice A: Lo que aún no sabemos (compilación general)

Esta es una lista maestra de todo lo que el proyecto aún no sabe, compilada de
todas las secciones de "Preguntas abiertas" del documento.

### Sobre el ciclo del puestero

- ¿Meses exactos de actividad en la montaña?
- ¿Días consecutivos sin bajar?
- ¿Actividad en mayo y octubre?

### Sobre validación RF

- ¿Alcance real de LoRa en Bardas Blancas?
- ¿Cantidad de repetidores necesarios?
- ¿Mejor frecuencia para el terreno?

### Sobre adopción

- ¿Los puesteros aceptarán usar el sistema?
- ¿Hay un líder comunitario que sea embajador?
- ¿Percepción del GPS como vigilancia?

### Sobre protocolo

- ¿Quién recibe la alerta?
- ¿Defensa Civil tiene capacidad de respuesta?
- ¿Qué pasa si nadie responde?

### Sobre institucional

- ¿Contacto con Auger, DS3, INTA?
- ¿Docente referente identificado?
- ¿Acta de creación firmada?

### Sobre financiamiento

- ¿Empresas locales dispuestas a sponsor?
- ¿Presupuesto anual definido?
- ¿Crowdfunding viable?

### Sobre infraestructura

- ¿Ubicaciones concretas para gateways redundantes?
- ¿Internet disponible en esas ubicaciones?
- ¿Quién administra cada gateway?

---

*Documento de Contexto Integral Red Cóndor — Versión 5.0 — Junio 2026*

*Colegio Diocesano San José — Malargüe, Mendoza, Argentina*

*Paulo Alvarez · alvarezpaulo82@gmail.com*

*Válido como contexto de trabajo para equipos humanos y sistemas de IA colaboradores.*
