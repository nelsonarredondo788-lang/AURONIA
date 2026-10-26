# Tarea: previs en arcilla (clay render) en Blender — prueba de control de cámara para Seedance 2.5

## Objetivo
Crear la pieza 1 del método de control de cámara con IA: una escena 3D simple en gris (sin texturas) con un movimiento de cámara preciso, renderizada como video «de arcilla». Ese video se combinará después con la imagen maestra del dúo (tablet + iPhone) en Seedance 2.5. **Esta tarea es SOLO la previs: nada fotorrealista.**

## Entorno
- Blender 5.2.2 (ya instalado). Proyecto: `C:\Users\Administrator\Documents\auron-video-blender\` (créalo si no existe).
- Todo se construye con un script de Python (bpy) guardado como `crear_escena_camara.py` en esa carpeta, para poder ajustar y repetir. Guarda la escena como `prueba-camara.blend`.

## Escena (graybox, un solo material gris «arcilla», fondo oscuro)
La escena es la **llegada del elenco de AURONÍA**: 7 personajes en semicírculo sobre una plataforma circular. En gris, sin detalle — solo las siluetas y las posiciones:
1. Plataforma circular grande (disco) como suelo, sobre un fondo/void oscuro.
2. **7 figuras «personaje»** en semicírculo mirando a cámara: cada una es una cápsula redondeada de ~1 unidad de alto con una esfera como cabeza (proporción de mascota: cuerpo 60%, cabeza 40%), todas del mismo tamaño. Sin rasgos, sin colores: gris arcilla.
3. La figura del **centro va un paso adelante** y es ~10% más alta (es el líder, Auron).
4. Iluminación de estudio suave (luces de área), render Workbench o Eevee con el material gris. Sin textos, sin logos, sin texturas.

## Cámara (lo importante)
- Formato: 1920×1080, 30 fps, duración **5 segundos** (150 frames).
- Lente constante de 35 mm — prohibido hacer zoom: solo movimiento físico.
- Trayectoria con easing suave (Bezier, entra y sale despacio, sin cortes):
  - **Inicio:** plano general — los 7 personajes completos en cuadro sobre la plataforma.
  - **Movimiento:** avance lento y majestuoso (push-in) hacia el personaje del centro, arqueando muy levemente (~10°) para dar profundidad.
  - **Final:** plano medio del líder al centro, con el resto del elenco visible a sus lados.
- Implementa la trayectoria con keyframes sobre un objeto Empty «meta» (en el líder) al que la cámara mire siempre (track-to), para que el encuadre nunca pierda al elenco.

## Flujo con compuerta (importante)
1. Primero renderiza SOLO 3 imágenes fijas: `frame-inicio.png` (frame 1), `frame-medio.png` (frame 75), `frame-final.png` (frame 150).
2. **DETENTE y reporta** con las 3 imágenes y los datos de la trayectoria (posición inicial/final de la cámara). Nelson aprueba los encuadres antes de renderizar el video.
3. Con la aprobación, renderiza `previs-arcilla.mp4` (H.264) y reporta su ruta y duración.

## Reporte final de esta fase
Script usado, ruta del .blend, las 3 imágenes, y cualquier ajuste que hayas tenido que hacer a las medidas o a la trayectoria.
