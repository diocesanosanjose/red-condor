# Propuestas de Aplicaciones para Red Cóndor
## Equipo 2: Energía

Basado en la investigación realizada sobre paneles solares, baterías, consumo del ESP32 y dimensionamiento de autonomía, proponemos las siguientes aplicaciones concretas para el **Proyecto Red Cóndor**. Estas propuestas conectan la tecnología de energía autónoma con las necesidades reales de usuarios en zonas rurales y de montaña de Malargüe y alrededores (puestos, rescatistas, Defensa Civil).

---

## 1. Nodos Sensores Autónomos Solares para Puestos Rurales (Productores Aislados)
**Descripción:**  
Dispositivos compactos alimentados por **panel monocristalino de 5-10 W + batería LiFePO4 de 10-30 Ah** con ESP32 en deep sleep + sensores ambientales (temperatura, humedad, presión, humedad de suelo) y módulo LoRa. 

**Funcionalidad para el usuario:**
- Monitoreo continuo de condiciones agroclimáticas (heladas, sequía, viento fuerte).
- Alertas automáticas vía red LoRa/radioenlaces a puestos vecinos o central de Defensa Civil.
- Datos históricos para planificación de siembras, pastoreo o protección de animales.

**Ventajas energéticas:**
- Autonomía de **4-7 días** sin sol (dimensionada para inviernos de Malargüe).
- Mantenimiento casi nulo (panel orientado norte a 35-40°, batería protegida del frío).
- Costo operativo muy bajo a 5-10 años (LiFePO4 dura miles de ciclos).

**Ejemplo de dimensionamiento:**  
Consumo estimado ~0.1-0.3 Wh/día → Panel 10 W + batería 20 Ah LiFePO4 + MPPT pequeño → Sistema completo < USD 150-250 (estimado, dependiendo de proveedores locales).

---

## 2. Estaciones de Monitoreo para Rescate y Defensa Civil en Zonas de Montaña
**Descripción:**  
Nodos más robustos con **panel de 10-20 W**, batería LiFePO4 de 30-60 Ah (o mayor), carcasa IP67 resistente a frío, viento y nieve, equipados con:
- Sensores ambientales + GPS.
- Posible cámara low-power o sensor de movimiento (para detección de avalanchas, animales o personas extraviadas).
- Transmisión LoRa + posibilidad de radioenlace punto a punto.

**Uso principal:**
- Datos en tiempo real para equipos de rescate (ubicación, condiciones meteo, riesgo de aludes).
- Monitoreo de ríos, caminos de montaña o zonas de alto riesgo.
- Apoyo a Defensa Civil para toma de decisiones (alertas tempranas).

**Características energéticas clave:**
- Sobredimensionamiento para **5+ días de autonomía** + heater de batería opcional.
- Posibilidad de agregar pequeño panel eólico complementario en sitios ventosos (común en Malargüe).
- Monitoreo remoto del estado de la batería y producción solar (reportado junto con datos ambientales).

---

## 3. Gateway / Repetidor Principal con Energía de Mayor Capacidad
**Descripción:**  
Nodo concentrador ubicado en punto estratégico elevado (buena visibilidad solar y radio). 
- **Panel solar:** 30-80 W monocristalino (o array pequeño).
- **Batería:** 100-200+ Ah LiFePO4 o banco modular.
- ESP32 o ESP32-S3 + LoRa gateway (recibe de decenas de nodos periféricos) + radioenlace hacia infraestructura central o internet (si disponible en algún punto).
- Posible integración con repetidor de Equipo Comunicaciones.

**Justificación energética:**
- Mayor consumo por estar siempre "escuchando" o procesando más datos.
- Permite centralizar información de toda la red de nodos y enviarla de forma eficiente.
- Redundancia: sistema híbrido solar + posible generador portátil de respaldo para emergencias prolongadas.

**Beneficio para Red Cóndor:**  
Actúa como "columna vertebral" energética y de comunicaciones, permitiendo que los nodos de campo sean ultra-bajos consumo.

---

## 4. Sistemas Híbridos Solares + Eólicos para Zonas de Alta Variabilidad
**Descripción:**  
En sitios con buen recurso eólico (característico de algunas áreas de Malargüe y pre-cordillera), complementar el panel solar con un **pequeño aerogenerador de 50-200 W** + regulador híbrido.

**Ventajas:**
- Mayor producción en invierno (cuando hay más viento y menos sol).
- Mayor resiliencia ante periodos nublados prolongados.
- Ideal para gateways o estaciones críticas de Defensa Civil.

**Nota:** Requiere estudio de recurso eólico local, pero es una propuesta de valor agregado para la siguiente etapa del proyecto.

---

## 5. Aplicaciones Transversales y de Valor Agregado
- **Monitoreo de infraestructura crítica:** Sensores de vibración/nivel en represas, canales o caminos remotos (alimentados con el mismo esquema de energía autónoma).
- **Apoyo al turismo y astronomía:** Estaciones meteo de bajo impacto visual para zonas de alto valor turístico/astronómico cerca de Malargüe (baja contaminación lumínica), con datos públicos vía dashboard web (ver Equipo Infraestructura).
- **Educación y capacitación:** Kits didácticos portátiles de energía solar + ESP32 para capacitar a productores rurales o equipos de rescate en el uso y mantenimiento básico del sistema.
- **Expansión futura:** Diseño modular que permita agregar fácilmente más sensores o capacidad de batería/panel según necesidades detectadas en campo.

---

## Beneficios Generales para el Proyecto Red Cóndor
| Aspecto                  | Beneficio de la propuesta de energía |
|--------------------------|--------------------------------------|
| **Autonomía**            | Nodos 100% independientes de red eléctrica (inexistente en la zona) |
| **Mantenimiento**        | Mínimo (5-10 años sin intervención mayor gracias a LiFePO4 + deep sleep) |
| **Costo a largo plazo**  | Bajo (evita generadores a combustible, baterías de plomo de corta vida) |
| **Escalabilidad**        | Fácil agregar nodos nuevos sin infraestructura eléctrica |
| **Sostenibilidad**       | 100% renovable, alineado con objetivos ambientales de áreas naturales |
| **Fiabilidad en frío**   | Diseñado específicamente para inviernos de Malargüe (LiFePO4 + protección térmica) |
| **Integración**          | Compatible con LoRa/radioenlaces (Equipo 1), hardware ESP32 (Equipo 3), usuarios reales (Equipo 4) e infraestructura backend (Equipo 5) |

---

## Recomendaciones para la Siguiente Etapa (Prototipado)
1. **Prototipo inicial:** Construir 2-3 nodos de prueba con:
   - ESP32 + LoRa + BME280
   - Panel monocristalino 10 W
   - Batería LiFePO4 20-30 Ah + MPPT
   - Medir consumo real durante 1-2 semanas (incluyendo días nublados simulados).
2. Validar orientación e inclinación en sitio real o con simulación.
3. Coordinar con Equipo Comunicaciones para definir perfil de tráfico LoRa y consumo asociado.
4. Documentar costos reales en Argentina y proveedores recomendados.
5. Elaborar manual simple de instalación y mantenimiento para usuarios finales (puestos, rescatistas).

Estas propuestas demuestran que es **totalmente viable y altamente recomendable** implementar un sistema de energía solar autónoma de bajo consumo para Red Cóndor, permitiendo llevar conectividad, monitoreo ambiental y apoyo a rescate a zonas donde hoy no existe ninguna infraestructura tecnológica.

---

*Documento elaborado por Equipo 2 - Energía | Proyecto Red Cóndor | Junio 2026*
