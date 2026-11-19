# Explorador de Movilidad Internacional — Uniandes (prototipo)

Aplicación pública de orientación para movilidad internacional hecha con React + Vite. **No es un sitio oficial ni confirma elegibilidad para intercambio.**

## ¿Qué incluye?
- Exploración por perfil (idioma, nivel, certificado, área, promedio y semestre).
- Búsqueda por universidad, relación y país.
- Fichas detalladas de requisitos de idioma y observaciones por relación.
- Identificación de registros revisados para 2027-20 y registros pendientes.
- Guardar relaciones durante la sesión (sin servidor ni cuentas; no persistente).
- Diseño responsive con identidad visual conceptual inspirada en Uniandes.
- GitHub Actions para publicación automática en GitHub Pages.

**Fuente:** `Base 1  de idioma - 202720.xlsx` suministrada para este desarrollo. Contiene 513 filas de relaciones, de las cuales 223 figuran como revisadas. Solo se exponen campos de requisitos y descripciones institucionales, no datos privados de estudiantes.

## Publicar en GitHub Pages (sin instalar nada)
1. Crea un repositorio nuevo en GitHub (por ejemplo `orientador-movilidad`). Puede ser público; verifica antes la autorización institucional para publicar los datos.
2. Descomprime el ZIP y sube **todos los archivos y carpetas de su interior** a la raíz del repositorio, incluida la carpeta oculta `.github` (importante). Confirma los archivos en la rama `main`.
3. En **Settings > Pages > Build and deployment**, selecciona **Source: GitHub Actions**.
4. En **Actions**, abre el flujo `Publicar en GitHub Pages` y comprueba el despliegue. Si el flujo no se inicia, ejecuta **Run workflow**.
5. Tu sitio quedará en `https://TU_USUARIO.github.io/orientador-movilidad/` (reemplaza el usuario y nombre de repositorio). El enlace final aparece en la sección Pages y en la acción de deploy.

El build usa `base: './'` para que los recursos funcionen dentro de un subdirectorio de GitHub Pages.

## Ejecutar localmente
```bash
npm install
npm run dev
```
Luego abre la URL indicada por Vite. Para generar la versión de publicación:
```bash
npm run build
```

## Actualizar datos
El catálogo está en `src/data/relaciones.json`. La estructura de cada relación es:
```json
{"id":"6117","university":"Aalto University","relation":"...","country":"Finland","reviewed":true,"languages":[{"language":"Inglés","official":true,"minimum":"B2","tests":"IELTS, TOEFL, TOEIC, Cambridge","url":"","validity":"Vigencia 2 años","uniandesSecondLanguage":false,"notes":"..."}],"academicRestriction":"","sourceRow":3}
```
Para una actualización masiva, vuelve a transformar el Excel respetando el esquema. No publiques documentos internos sin autorización. Comprueba las referencias y fechas antes de abrir el sitio a estudiantes.

## Restricciones conocidas
- No se conoce el catálogo completo de convenios activos, programas elegibles, cupos, promedios, semestre, equivalencias de exámenes ni fechas de convocatoria; por eso **no se calcula una elegibilidad total**.
- Los campos académicos del perfil se muestran como base para la próxima fase, pero no influyen en la clasificación hasta disponer de reglas verificadas.
- La clasificación preliminar de idioma se basa en el MCER de forma orientativa y **no sustituye** puntajes o excepciones. Si hay dudas, muestra necesidad de validación.
- Algunos requisitos mínimos están en texto libre: se identifican patrones A1–C2, pero condiciones específicas deben revisarse en las fichas.
- Una universidad puede figurar en múltiples relaciones con escuelas o requisitos distintos. No se fusionan.
- Los registros marcados «revisados» se refieren al Excel, **no** a la validez actual del convenio.
- GitHub Pages es estático; para incorporar cuentas, carga privada de archivos o panel de administración se requiere backend y controles de seguridad.

## Próxima fase recomendada
Conseguir base oficial de convenios, programas habilitados, requisitos de promedio/semestre, fechas, cupos y responsables. Modelar reglas académicas verificadas por convenio y periodo, junto con un mecanismo de revisión y versionamiento.
