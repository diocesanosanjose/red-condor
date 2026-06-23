# Preguntas Abiertas - Equipo 3 (Hardware)

Este documento contiene los interrogantes técnicos que el **Equipo 3** debe resolver antes de avanzar a la **Etapa 1 (Prueba de concepto)**. Dado que el proyecto se encuentra en **fase de diseño conceptual** y aún **no se ha adquirido hardware**, estas dudas son críticas para definir la primera compra [1].

## 1. Microcontrolador (ESP32)
* **Consumo Energético:** ¿Cuál es el modelo de **ESP32** (S3, C3 o estándar) que ofrece el mejor balance entre potencia de procesamiento y bajo consumo en modo *deep sleep*?
* **Ecosistema:** ¿Existen placas de desarrollo que ya integren el chip LoRa y el ESP32 para reducir fallas en las conexiones manuales?

## 2. GPS y Localización en Montaña
* **Efecto Cañón:** ¿Cómo se comportará la precisión de los módulos GPS en las zonas de **Bardas Blancas** donde las paredes de la montaña pueden bloquear satélites [2]?
* **Velocidad de Respuesta:** ¿Qué módulos garantizan un *Hot Start* rápido para no agotar la batería del nodo móvil cada vez que el puestero necesite enviar su ubicación?

## 3. Sensores Ambientales (Etapa 6)
* **Resistencia al Clima:** ¿Qué sensores de temperatura y humedad pueden operar de forma continua a **-20°C** sin descalibrarse durante los temporales invernales [1, 2]?
* **Interfaz de Comunicación:** ¿Es más eficiente utilizar sensores con protocolo **I2C** o **SPI** para minimizar la cantidad de cables necesarios dentro del dispositivo?

## 4. Protección y Carcasas (IP67)
* **Estanqueidad:** ¿Cómo asegurar el sellado de los puntos de salida para las antenas externas y los botones de pánico para cumplir con la norma **IP67** (protección total contra agua y polvo)?
* **Materiales:** ¿Qué filamentos de impresión 3D (ABS, ASA o PETG) ofrecen la mejor resistencia estructural y protección contra los rayos UV en la altura de Malargüe?
* **Condensación:** ¿Es necesario incluir válvulas de compensación de presión para evitar que la humedad interna dañe el **ESP32** debido a los cambios bruscos de temperatura?

## 5. Interacción de Usuario
* **Ergonomía:** ¿Cómo diseñar el botón de alerta para que un puestero pueda accionarlo de forma segura incluso usando **guantes de abrigo** pesados?

