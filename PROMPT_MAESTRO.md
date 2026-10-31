# PROMPT MAESTRO — MIS DIPLOMAS DOCENTES

Actuá como desarrollador/a senior de aplicaciones web, diseñador/a editorial especializado/a en diplomas escolares y QA engineer. Creá **directamente una aplicación web funcional, completa y lista para publicar en GitHub Pages**, llamada **MIS DIPLOMAS DOCENTES**.

**Entregable obligatorio:** un único archivo `index.html` con todo el HTML, CSS y JavaScript necesario. No quiero maquetas, explicaciones que sustituyan el archivo, código fragmentado ni instrucciones para armarlo manualmente. Si trabajás en un entorno que permite crear archivos, entregá directamente el `index.html` descargable. Usá JavaScript nativo; sin React, compiladores, backend, cuentas ni bases de datos. La app debe funcionar en computadoras y celulares. Podés usar Google Fonts con una alternativa local cuando no haya conexión, pero **las funciones de exportación no deben depender de CDNs ni de servicios externos**.

## 1. Objetivo

Permitir que una docente cree, personalice y descargue diplomas, certificados y reconocimientos individuales o masivos. Debe ser una herramienta visual, fácil de usar y suficientemente confiable como para generar 40 o más diplomas de una misma clase y entregarlos en un único PDF listo para imprimir.

## 2. Identidad y apariencia

Nombre y encabezado: **MIS DIPLOMAS DOCENTES**. Subtítulo: “Generador de certificados, diplomas y reconocimientos”. Interfaz limpia, profesional, agradable y con colores suaves. Dos columnas en escritorio: controles a la izquierda y vista previa grande a la derecha; distribución adaptable en celular.

Incluir siempre en el pie de la **aplicación**: **“Creado por HeyMissKite”**. Está estrictamente prohibido incorporar HeyMissKite, logos o marcas de agua propios **dentro de los diplomas exportados**. Los certificados son de las instituciones y docentes que los usan.

## 3. Datos editables

- Nombre de la institución y curso/grado.
- Nombre y apellido del estudiante.
- Tipo de documento: diploma de reconocimiento, certificado, certificado de finalización, certificado de promoción y título personalizado.
- Frase introductoria editable, por ejemplo “Se otorga a”.
- Reconocimiento desde opciones sugeridas o personalizado.
- Mensaje dedicatorio completamente editable; puede estar vacío.
- Fecha libre.
- Nombre/cargo de firmante 1 y firmante 2; si se deja vacío, usar un rótulo genérico sin inventar personas.
- Logo de la institución opcional.

## 4. Generación individual y masiva

Dos modos claramente identificados: **Individual** y **Masivo**. En el individual se escribe un estudiante. En masivo se pega una lista con un alumno por línea. Admitir dos formatos:

- `Nombre Apellido | Reconocimiento` para reconocimientos diferentes.
- `Nombre Apellido` para compartir un mismo reconocimiento, una certificación de finalización o una promoción.

Permitir elegir reconocimiento base. Quitar duplicados exactos sin borrar alumnos distintos; conservar tildes, comas, guiones y caracteres habituales. Mostrar número total de diplomas detectados, lista navegable y botones Anterior/Siguiente. Si se edita la lista, **actualizar los datos antes de exportar**; nunca imprimir una versión vieja. Un PDF masivo de 40 alumnos debe tener exactamente 40 páginas, una por diploma.

## 5. Diseños, fondos y personalización

Ofrecer siete estilos seleccionables y distinguibles: Elegante, Moderno, Acuarela suave, Clásico con laureles, Gradiente limpio, Infantil elegante y Minimalista. No usar decoraciones detrás de textos que dificulten la lectura. Los estilos deben verse también en el PNG y PDF; no exportar siempre el mismo diseño genérico.

Ofrecer orientación horizontal y vertical y paletas rápidas: celeste, dorado, lavanda, verde, rosa pastel, azul profundo, durazno y neutro. Permitir elegir color principal y suave manualmente.

**Diseño propio:** permitir subir una imagen JPG o PNG como fondo del diploma. Esa imagen solo aporta decoración, mientras que título, nombre, texto, fecha, logo y firmas siguen siendo editables desde la app. Debe haber botón Subir diseño, opción para activarlo/desactivarlo y botón Quitar diseño. Mostrarlo también en PNG y PDF. Ajustar el fondo para cubrir la hoja sin deformarlo, indicando si pudiera recortarse.

## 6. Tipografías: requisito crítico

Usar un selector **desplegable compacto** (similar al selector de estilos), no una grilla gigante. Cada opción debe mostrar su nombre normal y, a su lado, una muestra escrita con esa fuente. Incluir exactamente estas diez fuentes: Playfair Display, DM Serif Display, Cormorant Garamond, Lora, Merriweather, Montserrat, Raleway, Poppins, Quicksand y Manrope.

**El selector debe funcionar realmente:** al elegir una fuente, el título y el nombre del estudiante cambian visiblemente en la vista previa. El tipo seleccionado debe guardarse con los datos del diploma y conservarse tras recargar. La **misma familia tipográfica seleccionada** debe aplicarse a la exportación PNG y al PDF.

Importar fuentes desde Google Fonts en el HTML y esperar la carga real con `document.fonts.load` / `document.fonts.ready` antes de medir o pintar el texto de exportación. **No confiar en que un SVG cargado como imagen herede fuentes externas de la página:** para exportar, dibujar textos en Canvas 2D usando las fuentes cargadas o utilizar una técnica equivalente verificada. Si Google Fonts falla por falta de internet o un bloqueo, mostrar un aviso visible y utilizar una pila de fuentes alternativas legibles, sin fingir que la fuente remota está disponible.

Tres controles de tamaño independientes: **título**, **nombre** y **texto del mensaje**. Deben cambiar en el acto y su valor se debe respetar en vista previa y exportación. Probar cada uno con mínimo, medio y máximo; el cambio debe ser mensurable y visible. Mantener autoajuste solo como protección ante textos extraordinariamente largos; nunca reducir silenciosamente todas las opciones al mismo tamaño.

## 7. Composición profesional y vista previa

Distribuir los bloques con una secuencia y márgenes consistentes: institución → título → espacio claro → frase introductoria → nombre → línea cercana al nombre → reconocimiento → mensaje → curso/fecha → firmas.

La firma 1 y la firma 2 deben estar a **la misma altura**, cada una arriba de su línea. Reservar márgenes seguros alrededor del marco. Nunca dejar título, nombre, línea, mensaje, curso, fecha o firmas afuera del área imprimible. Evitar grandes huecos innecesarios o textos solapados. Adaptar texto a los anchos disponibles mediante medición real de caracteres, sin cortar nombres ni dedicatorias. Si los datos son demasiado largos para una sola página, advertirlo explícitamente y pedir reducirlos antes de exportar, en lugar de truncarlos en silencio.

La vista previa debe representar fielmente el resultado final: mismos fondos, posiciones aproximadas, tipografía, tamaños y firmas. Comprobar tanto orientación horizontal como vertical y nombres largos.

## 8. Logo y dos firmas

Para cada una de las **dos** firmas ofrecer: “Subir firma”, “Firmar acá” (área de dibujo con mouse o dedo) y “Quitar”. Al subir fotografía o escaneo sobre papel blanco, intentar eliminar automáticamente el fondo blanco y conservar los trazos. No distorsionar la firma ni hacerla cruzar la línea. Poder usar una firma docente y otra de dirección/coordinación. Los nombres/cargos van debajo de su línea correspondiente. Ambos controles deben funcionar de manera independiente y exportarse correctamente.

## 9. Descargas e impresión

- Botón **Descargar como imagen**: archivo PNG individual de calidad para imprimir en A4 a 300 DPI; horizontal **3508 × 2480 px** o vertical **2480 × 3508 px** aproximadamente.
- Botón **Descargar PDF**: archivo PDF individual real, A4, de una página, sin abrir ventanas emergentes.
- Botón **Descargar todos en PDF**: UN solo PDF A4 multipágina, cada diploma en su propia página, adecuado para impresión masiva; verificar 10 y 40 alumnos.

Generar los PDF dentro del navegador a partir de imágenes renderizadas, mediante código local incluido en `index.html` o una solución igualmente independiente y probada. No depender de librerías externas que, al bloquearse, dejen botones sin funcionar. Manejar errores con avisos claros. No inventar mensajes de “Descargado” si la descarga falló. Las imágenes no pueden perder firmas, logos, fondos ni tipografías elegidas.

## 10. Datos demo, guardado y plantillas

Al primer uso mostrar datos ficticios de prueba y un distintivo “MODO DEMO”. Usar exclusivamente instituciones inventadas, por ejemplo “Colegio Horizonte Demo”; estudiante “Martina Suárez”. Agregar un botón **Eliminar datos de prueba** que limpie esos datos y evite que reaparezcan al recargar. Agregar botón **Nuevo** para vaciar el documento actual sin destruir las plantillas.

Persistir configuraciones y datos en el navegador con `localStorage` y manejar errores de almacenamiento. Permitir guardar, cargar y eliminar plantillas personalizadas. Cuando los archivos de imagen sean demasiado grandes para la cuota local, mostrar una advertencia y no indicar falsamente que se guardaron.

## 11. Diseño responsivo, accesibilidad y rendimiento

Usar etiquetas en español argentino, controles claros, estados visibles, botones y selectores accesibles por teclado, mensajes de confirmación y una interfaz adaptable a celular. No usar datos privados en ejemplos. Debe funcionar como sitio estático de GitHub Pages con un único `index.html` en la raíz, sin servidor ni compilación. Las fuentes externas pueden necesitar conexión, pero el resto de funciones deben ser locales.

## 12. Pruebas obligatorias antes de entregar

Ejecutar pruebas reales con navegador cuando esté disponible y revisar al menos estos casos:

1. Carga inicial sin excepciones JavaScript ni elementos DOM faltantes/duplicados.
2. Modo demo, eliminación irreversible de datos de prueba y botón Nuevo.
3. Selector de las diez tipografías: cambia selección, muestra muestra correcta, cambia el título/nombre, persiste, y cambia el archivo exportado cuando las fuentes están disponibles.
4. Sliders de título, nombre y texto en sus valores mínimo/medio/máximo; diferencias reales tanto en vista previa como en descarga.
5. Los siete estilos producen siete exportaciones visualmente distintas.
6. Horizontal y vertical, nombre largo, título largo, mensaje vacío y mensaje largo sin cortes ni solapamientos.
7. Una firma subida; dos firmas subidas; firma dibujada con mouse y tacto; quitar cada firma.
8. Fondo propio y logo subidos; activar, desactivar y eliminar el fondo sin perder datos.
9. Plantillas: guardar, cargar, borrar y recuperar datos de una sesión posterior.
10. PNG legible y dimensiones A4 300 DPI.
11. PDF individual de una página válido.
12. PDF masivo de 10 y de 40 alumnos, con cantidades de páginas correctas y sin mezclar alumnos.
13. Validar diferencias entre vista previa y descarga y corregir cualquier texto, firma o imagen desalineados.

**Criterio de entrega:** dar el archivo `index.html` final y un informe breve que distinga qué pruebas se hicieron realmente, cuáles pasaron y qué limitación externa no pudo verificarse. No prometer “100 % probado” si una prueba no se ejecutó. Mantener el producto estable y no cambiar arbitrariamente diseños ni funciones que ya trabajan bien.
