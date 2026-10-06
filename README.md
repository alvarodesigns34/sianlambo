# Sián FKP 37 — reconstrucción exterior en Blender

**Estado: primera reconstrucción propia a escala real; trabajo en progreso.**

Este proyecto contiene un modelo editable del Lamborghini Sián FKP 37 coupé, una exportación GLB y renders realizados con Cycles. Se ha construido con topología propia, superficies paramétricas, piezas independientes y texturas PBR originales. No importa mallas de videojuegos ni el modelo AR del fabricante.

**Esta versión todavía no alcanza una réplica ultrarrealista y exacta, sin simplificaciones.** Las dimensiones generales están verificadas; las curvaturas, las relaciones entre paneles y numerosos detalles se han interpretado a partir de fotografías. El interior y los elementos mecánicos ocultos son parciales. Véase [el estado de fidelidad](docs/fidelity.md).

![Vista frontal de la reconstrucción](renders/front_three_quarter.png)

## Archivos

| Archivo | Uso |
|---|---|
| [model/sian_fkp37.blend](model/sian_fkp37.blend) | Modelo principal, materiales, texturas empaquetadas, iluminación y seis cámaras |
| [model/sian_fkp37.glb](model/sian_fkp37.glb) | Geometría completa exportada, sin reducción de polígonos, con materiales PBR |
| [model/textures](model/textures) | Mapas originales de carbono, rugosidad y microtextura de pintura y caucho |
| [renders](renders) | Frente, lateral, parte superior, dos vistas de tres cuartos y detalle de rueda |
| [docs/verification.json](docs/verification.json) | Mediciones de la geometría real y comprobaciones del archivo |
| [scripts](scripts) | Generación y acabado reproducibles |

La escena usa **1 unidad de Blender = 1 metro**. Eje X transversal, Y longitudinal (frontal hacia −Y) y Z vertical. El GLB emplea la convención Y vertical de glTF y vuelve a estos ejes al importarlo en Blender.

## Contenido

- Paneles exteriores y pasos de rueda, bonnet, techo y túnel central Periscopio.
- Tomas laterales, splitter, rejillas de celdas hexagonales, lamas del motor, aletas térmicas y difusor con tabiques independientes.
- Firma luminosa delantera en Y, seis luces traseras hexagonales, reflectores y proyectores.
- Llantas con radios dobles, neumáticos de medidas nominales 255/30 ZR20 y 355/25 ZR21, surcos, marcajes y válvulas.
- Discos, perforaciones, pinzas, tornillería y latiguillos visibles.
- Espejos, limpiaparabrisas, sensores, tapa de combustible y escapes hexagonales con paredes interiores.
- Materiales que interpretan Verde Gea, Oro Electrum, carbono tejido, vidrio, caucho, titanio y cuero.

Los materiales de pintura y cuero contienen variaciones procedimentales adicionales en el `.blend`. El GLB conserva el carbono y las microtexturas mediante mapas PBR, con una aproximación uniforme al color de la pintura. No todos los motores reproducen de la misma manera la transparencia, el clearcoat o la emisión.

## Escala de control

| Medida | Objetivo |
|---|---:|
| Longitud | 4,979 m |
| Anchura de carrocería | 2,080 m |
| Anchura con retrovisores | 2,265 m |
| Altura | 1,134 m |
| Batalla | 2,700 m |

Se han usado los datos publicados actualmente por [Lamborghini](https://www.lamborghini.com/en-en/models/few-off/sian-fkp-37), consultados el 6 de octubre de 2026. Algunas fichas de lanzamiento publican medidas ligeramente diferentes; aquí no se mezclan con los controles de la ficha actual. Las dimensiones de control no certifican la exactitud local de las superficies.

## Abrir o regenerar

Abre `model/sian_fkp37.blend` con Blender 4.5 LTS o posterior. Las texturas están empaquetadas; no se necesita descargar recursos para abrirlo. La colección `90_STUDIO` está oculta en el visor de edición y disponible para renderizar.

Para regenerar los archivos en Windows, con Blender ya instalado o descargado:

```powershell
.\scripts\build.ps1 -Blender 'C:\ruta\a\blender.exe'
```

Añade `-Render` para regenerar también las seis imágenes. El proceso usa Python y NumPy incluidos en Blender. Los scripts no descargan modelos, imágenes ni dependencias. La generación intermedia se guarda en `.work/`, fuera del seguimiento de Git.

## Referencias y siguiente trabajo

Las fuentes, criterios de color y límites de verificación se documentan en [docs/references.md](docs/references.md). El siguiente paso necesario es contrastar y reconstruir las superficies con documentación geométrica más completa o un escaneo autorizado, cerrar las uniones y completar los microdetalles exteriores enumerados en [docs/fidelity.md](docs/fidelity.md).

El diseño del vehículo y los nombres de las marcas pertenecen a sus respectivos titulares. Este estudio es independiente y no está certificado ni patrocinado por Lamborghini.
