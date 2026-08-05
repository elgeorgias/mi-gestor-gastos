# Gestor de Gastos y Finanzas Personal (GitHub Pages)

Aplicación web progresiva (PWA) optimizada y responsive para PC y dispositivos móviles, diseñada para ser alojada en GitHub Pages.

## ✨ Características

- **Diseño Adaptativo / Responsive:** Interfaz moderna con soporte completo para pantalla de PC y pantallas táctiles de móviles.
- **Importación Limpia de CSV:** Lee únicamente los datos de **Concepto**, **Fecha** y **Cantidad / Importe** (omite el saldo en cuenta).
- **Categorización en 2 Niveles:**
  - **Categoría 1 (Principal):** Alimentación, Vivienda, Seguros y Servicios, Transporte, Inversiones y Ahorro, Actividades y Ocio, Suscripciones, Ingresos, Otros.
  - **Categoría 2 (Detalle / Subcategoría):** Supermercado, Restaurante, Club/Deportes, Hotel/Apartamento, Gasolina, Fondos, etc.
- **Gráficos e Informes Interactivos:** Visualización con Chart.js con la posibilidad de conmutar la visión del gráfico entre Categoría 1 y Categoría 2, así como filtrado por clics en porciones del gráfico o tabla de totales.
- **Exportación:** Permite descargar los datos clasificados en formato Excel (`.xlsx`).
- **Persistencia Local:** Tus datos se guardan de forma privada en el almacenamiento local del navegador (`localStorage`).