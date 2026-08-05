# Gestor de Gastos y Finanzas Personal (GitHub Pages)

Aplicación web progresiva (PWA) optimizada y responsive para PC y dispositivos móviles, diseñada para ser alojada en GitHub Pages.

## ✨ Características

- **Diseño Adaptativo / Responsive:** Interfaz moderna con soporte completo para pantalla de PC y pantallas táctiles de móviles.
- **Importación Limpia de CSV:** Lee únicamente los datos de **Concepto**, **Fecha** y **Cantidad / Importe** (omite el saldo en cuenta).
- **Fechas Aplicables y Notas Personalizadas:**
  - Selector de **Fecha Aplicable** editable por movimiento para contabilidad por devengo.
  - Campo libre de **Notas** por movimiento con persistencia al guardar y al exportar.
- **Categorización en 2 Niveles Actualizada:**
  - **Compras:** Ropa, Electrónica, Otros.
  - **Transfer/Traspasos:** Gastos, Ingresos, Entre cuentas (*No computable* en las gráficas de ingresos/gastos).
  - Y el resto de categorías principales (*Alimentación, Vivienda, Seguros y Servicios, Transporte, Inversiones, Actividades y Ocio, Suscripciones, Ingresos, Otros*).
- **Gráficos e Informes Interactivos:** Visualización interactiva con Chart.js y tabla de desglose por categoría.
- **Exportación Completa:** Descarga de los movimientos clasificados en formato Excel (`.xlsx`) incluyendo Fecha Original, Fecha Aplicable, Categorías, Cantidad y Notas.
- **Persistencia Local:** Tus datos se guardan de forma privada en el almacenamiento local del navegador (`localStorage`).