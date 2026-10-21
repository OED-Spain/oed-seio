# oed-seio

Web del Grupo de Trabajo de Diseño de Experimentos (OED) de la Sociedad de Estadística e Investigación Operativa (SEIO).

Dirección: <https://oed-spain.github.io/oed-seio/>

La web está hecha con [Jekyll](https://jekyllrb.com/), que GitHub Pages compila automáticamente: basta con guardar un cambio en la rama `main` y en uno o dos minutos aparece publicado. No hace falta instalar nada para editar contenido.

## Cómo está organizada

```
_config.yml          Título, correo, dirección de la web y del repositorio
_data/               CONTENIDO QUE SE ACTUALIZA (miembros, eventos, software...)
  miembros.yml
  eventos.yml        Próximo evento y ediciones del congreso JEDE
  seminarios.yml
  software.yml
  lineas.yml         Líneas de investigación
  entidades.yml      Logos de la portada
  coordinacion.yml
  navegacion.yml     Menú
_layouts/default.html  Estructura común de todas las páginas
_includes/           Cabecera, pie y piezas reutilizadas
  iconos/            Dibujos de las ciudades del JEDE
assets/
  css/estilos.css    Todos los estilos
  fonts/             Tipografías (Rubik y Atkinson Hyperlegible, licencia OFL)
  logos/             Logos del grupo (svg, png, pdf) y de entidades
  img/               Imágenes y favicon
index.html           Inicio
quienes-somos/       Quiénes somos y miembros
lineas/              Líneas de investigación
software/            Software
eventos/             Eventos
contacto/            Contacto
```

La cabecera, el menú y el pie están en un único sitio (`_includes/cabecera.html` y `_includes/pie.html`): si se cambian ahí, cambian en todas las páginas.

## Editar contenido desde GitHub (sin instalar nada)

1. Abrir el archivo en GitHub, por ejemplo `_data/miembros.yml`.
2. Pulsar el lápiz (*Edit this file*).
3. Hacer el cambio y pulsar *Commit changes*.
4. Esperar uno o dos minutos y recargar la web. En la pestaña *Actions* del repositorio se ve si la publicación ha ido bien (marca verde) o ha fallado (cruz roja).

Los archivos `.yml` son texto con un formato sencillo, pero **la sangría importa**: hay que respetar los espacios del principio de cada línea (dos espacios, nunca tabuladores). Si un texto contiene dos puntos seguidos de espacio (`: `) o empieza por `[`, hay que ponerlo entre comillas.

### Añadir un miembro

En `_data/miembros.yml`, añadir un bloque como este en cualquier parte de la lista (la web los ordena sola por apellido):

```yaml
- nombre: Ana
  apellidos: García López
  afiliacion: Universidad de Oviedo
  orcid: 0000-0002-1825-0097
  scholar: https://scholar.google.com/citations?user=XXXXXXXXXXXX
```

- `orcid`, `scholar` y `web` son opcionales; si no se ponen, no aparece el botón.
- Si se deja `afiliacion: ""`, la web muestra «[Universidad o centro]».
- Si un apellido empieza por partícula y debe ordenarse por la palabra siguiente, se añade `orden: García López` (ver el ejemplo de «de la Calle Arroyo»).
- No se ponen correos ni otros datos personales: el repositorio es público.

### Añadir un seminario

En `_data/seminarios.yml`, sustituir `[]` por la lista de seminarios (o añadir uno más al final):

```yaml
- fecha: 2026-11-20
  titulo: Diseños óptimos para modelos de mezcla
  ponente: Ana García López
  afiliacion: Universidad de Oviedo
  modalidad: En línea
  enlace: https://...
```

La fecha va siempre como `AAAA-MM-DD`; la web la muestra como «20 noviembre 2026» y ordena los seminarios del más reciente al más antiguo. `enlace` (diapositivas o grabación) es opcional.

### Cambiar el próximo evento

En `_data/eventos.yml`, bloque `proximo`: fechas, lugar, web... Aparece en la portada y en Eventos. Si no hay ningún evento previsto, basta con poner `mostrar: false` dentro del bloque y la sección desaparece de las dos páginas; con `mostrar: true` vuelve a aparecer.

### Añadir una edición del JEDE

Cuando se celebre el congreso, en `_data/eventos.yml` añadir la edición **al principio** de la lista `jede`:

```yaml
jede:
  - edicion: VIII
    anio: 2027
    ciudad: Oviedo
    icono: generico
    web: https://...
```

`icono` es el nombre de un dibujo de `_includes/iconos/` sin la extensión. Para una ciudad nueva se puede usar `generico` o crear su dibujo (un archivo `.svg` con trazos para una cuadrícula de 48 × 48, como los existentes).

### Software, líneas de investigación y entidades

Mismo procedimiento con `_data/software.yml`, `_data/lineas.yml` y `_data/entidades.yml`; cada archivo explica sus campos en los comentarios del principio. Los logos de entidades se suben a `assets/logos/entidades/` y se indican con `logo: entidades/nombre.svg`.

## Licencia

El código se distribuye bajo la licencia MIT (ver `LICENSE`). El contenido (textos e imágenes) se distribuye bajo CC BY 4.0, salvo los logotipos, que son propiedad de sus titulares. Las tipografías Rubik y Atkinson Hyperlegible se distribuyen bajo la SIL Open Font License 1.1 (ver `assets/fonts/`).
