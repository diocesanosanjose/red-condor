# Investigación Equipo 1: Comunicaciones - Red Cóndor

## 1. LoRa

**¿Cómo funciona LoRa?**  
LoRa (Long Range) es una tecnología inalámbrica de bajo consumo y largo alcance que utiliza modulación de espectro ensanchado basada en **Chirp Spread Spectrum (CSS)**.

**Chirp Spread Spectrum (CSS):**  
Consiste en enviar "chirps" (pulsos cuya frecuencia varía linealmente en el tiempo). Esto distribuye la señal en un ancho de banda amplio, haciéndola muy resistente al ruido, interferencias y desvanecimientos. Permite comunicación confiable incluso con señales muy débiles.

**Frecuencias en Argentina (ENACOM):**  
Banda principal sin licencia: **915 - 928 MHz** (plan AU915). Es la recomendada para Red Cóndor.

**Alcance en condiciones reales:**  
- Línea de vista ideal / terreno plano: 10-60 km.  
- Terreno montañoso o con obstáculos: 1-10 km por salto (depende de altura de antenas y spreading factor).  
En Malargüe se espera necesidad de repetidores.

## 2. Radioenlaces y Redes Mesh

**Radioenlaces punto a punto:**  
Transmisión directa entre dos puntos sin infraestructura intermedia. Requiere visibilidad directa (línea de vista) y antenas alineadas.

**Red Mesh:**  
Topología descentralizada donde **cada nodo puede recibir y retransmitir** mensajes. Los paquetes saltan de nodo en nodo hasta llegar al destino.  
**Ventajas:** Alta resiliencia (si un nodo falla, la ruta se reorganiza automáticamente). Ideal para zonas rurales/montañosas sin infraestructura.

Meshtastic es una implementación de red mesh sobre LoRa.

## 3. Antenas

**Tipos principales:**
- **Omnidireccionales**: Cubren 360°. Ideales para nodos móviles y repetidores centrales.
- **Direccionales** (Yagi, panel): Concentran la señal en una dirección. Mayor alcance en enlaces específicos.

**Ganancia (dBi):**  
Indica cuánto "enfoca" la antena la energía. Mayor dBi = más alcance en la dirección principal, pero menos cobertura angular.

**Recomendación para montaña:**
- Nodos puesteros: Omni 2-5 dBi (portátil).
- Repetidores elevados: Omni 5-9 dBi o direccionales para corredores.

## 4. Cobertura y Factores Geográficos

**Factores clave que afectan la propagación:**
- **Relieve/montañas**: Bloquean señales (efecto sombra). La elevación de antenas es crítica.
- **Vegetación**: Absorbe especialmente en frecuencias altas.
- **Clima**: Lluvia, nieve, niebla y humedad reducen el alcance. Viento tiene menor impacto.
- Regla general: Menor frecuencia = mejor penetración.

## 5. Repetidores

Se instalan en puntos altos para "ver" varios nodos. En mesh cada nodo repite, pero repetidores fijos solares extienden cobertura significativamente.  
Cantidad estimada inicial para Bardas Blancas: 2-4 según pruebas de campo.

**Fuentes principales:** Semtech, Meshtastic docs, ENACOM, pruebas de campo reportadas.
