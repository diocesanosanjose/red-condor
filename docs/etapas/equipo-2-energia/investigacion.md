# Equipo 2: Energía - Investigación

## Paneles Solares

**Tipos principales:**
- **Monocristalino**: Hechos de un solo cristal de silicio puro. Color negro uniforme.
- **Policristalino**: Hechos de múltiples cristales de silicio. Color azul más brillante y aspecto "cuadriculado".

**Comparación:**
- **Eficiencia**: Monocristalino 18-22% | Policristalino 15-17%.
- **Rendimiento**: El monocristalino genera más energía en el mismo espacio y funciona mejor con poca luz y en temperaturas frías.
- **Precio**: Monocristalino más caro.
- **Recomendación para Red Cóndor**: Usar **monocristalino** por su mejor rendimiento en clima frío y espacio reducido (paneles portátiles o en repetidores).

**Orientación en Malargüe (latitud ≈ 35.5°S):**
- Orientar hacia el **Norte** (azimut 0°).
- Inclinación ideal: 30°-40° (aprox. latitud + 5-10° para invierno).
- En verano se puede ajustar a menor inclinación.

**Potencia recomendada:**
- Nodo móvil: Panel plegable 5W.
- Repetidor fijo: 10W-20W.

## Baterías

**Tecnologías principales:**
- **Plomo-ácido** (tradicional): Barata, pero pesada, corta vida (300-800 ciclos), mal en frío.
- **Li-Ion** (convencional): Buena densidad energética, pero sensible a temperaturas extremas.
- **LiFePO4** (fosfato de hierro y litio): La mejor opción actual.

**Recomendación para Malargüe (frío extremo -20°C):**
- **LiFePO4** es claramente superior.
  - Excelente rendimiento en frío.
  - 2000-5000 ciclos de vida (mucho más duradera).
  - Más segura (menor riesgo de incendio).
  - Puede descargarse al 80-90% sin daño.

## Consumo Energético del ESP32 + LoRa (Meshtastic)

- **Deep Sleep**: 10-150 µA (ideal: ~20-50 µA en placas optimizadas).
- **Light Sleep**: ~0.8-1 mA (CPU suspendida, radio LoRa activa).
- **Activo / Transmisión**: 100-150 mA (picos).
- **Consumo promedio real** (con buena configuración): 2-5 mA.

**Cómo reducir consumo:**
- Usar **Deep Sleep** + wake-up por timer.
- Desactivar Bluetooth y GPS cuando no se necesiten.
- Configurar intervalos largos de transmisión (cada 30-60 min).
- Meshtastic tiene modos de ahorro de energía específicos.

## Autonomía y Dimensionamiento

**Fórmula básica de autonomía:**
