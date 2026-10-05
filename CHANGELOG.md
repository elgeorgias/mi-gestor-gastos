# Registro de Cambios (Changelog)

Todos los cambios notables en este proyecto serán documentados en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/),
y este proyecto se adhiere a [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Sin publicar] - [Unreleased]

### Añadido
- **Exportación e Importación de Categorías en Base de Datos:**
  - Inclusión de la estructura canónica y personalizada de categorías en la hoja `Categorías` del libro Excel `.xlsx` generado.
  - Inclusión de `categorias_[timestamp].json` y `estructura_categorias.json` dentro del archivo ZIP de copia de seguridad.
  - Soporte de importación de categorías desde libros Excel (`.xlsx`, `.xls`), archivos `.zip`, y archivos `.json`.
  - Persistencia prioritaria en `localStorage` (`finanzas_pwa_categorias`) para garantizar que las categorías importadas o editadas persistan tras recargar la página.
- **Documentación Técnica:**
  - Creación del archivo `MEMORY.md` como guía técnica completa del funcionamiento interno del sistema.
  - Actualización de `.junie/AGENTS.md` con las nuevas especificaciones de desarrollo y pruebas.

### Modificado
- **Lógica de Computabilidad de la Categoría `Transfer`:**
  - Dentro de la categoría principal `Transfer`, únicamente la subcategoría `Entre cuentas` (y sinónimo histórico `Propias`) es considerada no computable (`no-computables`), mostrándose en gris (`.amount-neutral`) y acumulándose exclusivamente en el total "No computable".
  - El resto de subcategorías (`Gastos`, `Ingresos` u otras personalizadas) son plenamente computables en ingresos o gastos, mostrándose en verde o rojo/naranja en la tabla, contando para el balance neto y reflejándose en las gráficas de totales y desglose por categorías (con color morado distintivo `#8b5cf6`).
  - Corrección en `loadData()` para preservar permanentemente la subcategoría `cat2` asignada por el usuario en transferencias en lugar de forzarla a `Entre cuentas`.

---

## [1.0.0] - 2026-08-23

### Añadido
- **Soporte Multi-Banco para Importación:**
  - Ingesta automática de extractos en formatos CSV, XLS y XLSX.
  - Adaptadores específicos y robustos para:
    - **CaixaBank** (CSV desde app móvil y formatos XLS).
    - **Bankinter** (Excel XLS/XLSX desde banca web).
    - **Banco Sabadell** (Excel XLS desde banca web).
    - **ING** (Excel XLS con detección de fechas en nombre y contenido).
    - **OpenBank** (Excel XLS y soporte para transacciones exportadas).
    - **Pluxee** (CSV y Excel XLSX exportados desde app móvil).
- **Categorización en Dos Niveles:**
  - Sistema jerárquico de Categoría Principal (`cat1`) y Subcategoría (`cat2`).
  - Archivo canónico `categorias/estructura_categorias.json` y soporte de categorías personalizadas guardadas en `localStorage`.
  - Heurística de auto-categorización (`clasificarAuto`) basada en conceptos bancarios frecuentes.
  - Modal de gestión de categorías y subcategorías con generación dinámica de colores pastel/HSL.
- **Deduplicación Inteligente de Movimientos:**
  - Detección de duplicados en la importación mediante firma compuesta normalizada (`fecha` + `concepto` + `importe`).
  - Soporte de multiconjunto / frecuencias para preservar transacciones legítimas idénticas del mismo día.
- **Filtros Avanzados y Búsqueda:**
  - Presets de rango de fechas (mes actual, mes anterior, año completo, año anterior, etc.).
  - Filtros independientes por columna (Fecha, Origen, Propietario, Concepto, Categoría, Importe, Notas, Revisado).
  - Búsqueda global instantánea en tiempo real.
- **Edición y Acciones en Lote:**
  - Modificación en línea de fecha contable aplicable, notas, categorías y estado revisado.
  - Acciones masivas: asignar categoría principal/subcategoría a filas seleccionadas, marcar como revisado/pendiente y eliminación en lote.
- **Informes Visuales y Gráficos:**
  - Integración con Chart.js para dashboards financieros.
  - Gráfico de barras de evolución temporal (ingresos, gastos fijos, gastos variables, transferencias).
  - Gráfico de desglose por categoría principal (`Cat1`) y subcategorías (`Cat2`) con paletas de color asignadas.
  - Tarjetas de resumen con totales de ingresos, gastos, transferencias y balance neto.
- **Exportación y Copia de Seguridad Completa (ZIP Bundle):**
  - Exportación empaquetada con JSZip que incluye:
    - Libro Excel (`.xlsx`) con múltiples hojas formateadas mediante SheetJS.
    - Archivo CSV delimitado por comas (`Movimientos_Clasificados.csv`).
    - Copia de seguridad en JSON de la base de datos (`finanzas_db.json`).
    - Historial de importaciones (`historial_importaciones.json`).
    - Información del estado de la app y metadatos (`info_app.json`).
- **Historial y Auditoría de Importaciones:**
  - Registro de archivos importados previamente para evitar reimportaciones accidentales.
  - Modal visual para consultar el historial de ficheros importados.
- **Diseño Responsivo y Privacidad Total:**
  - Interfaz SPA / PWA optimizada para escritorio y móviles con tema oscuro, desenfoques y efectos glassmorphism.
  - Almacenamiento 100% local en el navegador (`localStorage`) sin envío de datos a servidores externos.
  - Indicador de versión de la aplicación (`APP_VERSION`) visible en la barra superior.
