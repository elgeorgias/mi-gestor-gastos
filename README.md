# Expense and Personal Finance Manager (Gestor de Gastos) `v1.0.0`

A responsive Progressive Web App (PWA) optimized for both PC and mobile devices, designed for easy hosting on GitHub Pages. This tool helps you track expenses, categorize movements, and visualize your financial health with complete privacy—all data stays in your browser.

## ✨ Features

- **Responsive Design:** Modern interface with full support for desktop and mobile touchscreens.
- **Privacy First:** Data is stored locally in your browser's `localStorage`. No data is sent to any server.
- **Clean CSV Import:** Smartly reads **Concept**, **Date**, and **Amount** from bank exports (tested with CaixaBank and others).
- **Customizable Movements:**
  - Editable **Applicable Date** for accrual accounting.
  - Custom **Notes** field for each movement that persists across sessions and exports.
- **2-Level Categorization & Smart Computability:**
  - **Main Categories:** Compras, Alimentación, Vivienda, Seguros y Servicios, Transporte, Inversiones y Ahorro, Actividades y Ocio, Suscripciones, Ingresos, Transfer, Otros, Salud.
  - **Sub-categories:** E.g., Compras (Ropa, Electrónica, Otros), Transfer (Gastos, Ingresos, Entre cuentas).
  - **Transfer Computability:** Within `Transfer`, only `Entre cuentas` is marked as non-computable (displayed in grey as neutral internal transfers). Subcategories such as `Gastos` and `Ingresos` are fully computable, color-coded accordingly, and included in the balance and visual charts.
- **Interactive Reports:** Visual insights powered by Chart.js and detailed category breakdown tables with distinct color coding (including custom purple tones for transfers).
- **Advanced Export & Full Backup:**
  - Export your database in a compressed ZIP package containing:
    - Multi-sheet Excel workbook (`.xlsx`) with `Movimientos`, `Últimos Movimientos`, `Historial Importaciones`, `Categorías`, and `Info App`.
    - CSV (`Movimientos_Clasificados.csv`) with UTF-8 BOM.
    - JSON database backup (`finanzas_db.json`), categories structure (`categorias.json`), import history, and app metadata.
- **Comprehensive Database Import:** Import database backups from `.xlsx`, `.xls`, `.zip`, `.json`, or `.csv` files. The category structure is automatically restored and persisted in `localStorage`.

## 🛠 Tech Stack

- **Frontend:** HTML5, CSS3 (Modern UI with backdrop blur and radial gradients).
- **Language:** Vanilla JavaScript (ES6+).
- **Libraries (via CDN):**
  - [Chart.js](https://www.chartjs.org/) - For interactive charts.
  - [PapaParse](https://www.papaparse.com/) - For robust CSV parsing.
  - [SheetJS (xlsx)](https://sheetjs.com/) - For Excel file generation and parsing.
  - [JSZip](https://stuk.github.io/jszip/) - For zip archive packaging and extraction.
- **Storage:** Browser `localStorage`.

## 🚀 Getting Started

### Requirements
- A modern web browser (Chrome, Firefox, Safari, Edge).
- No server or build tools required.

### Setup & Run
1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/mi-gestor-gastos.git
   ```
2. Open `index.html` directly in your browser.
   - *Alternatively*, serve it using a simple local server like `live-server` or Python's `http.server`:
     ```bash
     python3 -m http.server 8000
     ```

## 📂 Project Structure

- `index.html`: The main entry point containing the UI, CSS styles, and application logic.
- `CHANGELOG.md`: Record of all notable changes and version releases.
- `MEMORY.md`: Detailed technical specification and system operational reference.
- `categorias/`: Configuration files for the categorization engine.
  - `estructura_categorias.json`: Current active canonical category structure.
- `exports-app/`: (Symlinked/Local) Recommended directory for saving your exported CSV/Excel files and database backups.
- `manifest.json` (inline): Basic PWA configuration for "Add to Home Screen" support.
- `.junie/AGENTS.md`: Developer guidelines, testing instructions, and codebase conventions.

## 📝 Scripts & Development
- **Changelog:** All updates, new features, and fixes are tracked in [CHANGELOG.md](CHANGELOG.md) following Keep a Changelog conventions.
- **Testing:** Unit tests for data structures and parsing can be run with Python or JavaScriptCore / Node.js.
- **Builds:** No build process required (Static HTML/JS).

## 🔐 Environment Variables
No environment variables are required as the application runs entirely client-side.

## 📜 License
This project is for personal use. TODO: Add a formal LICENSE file (e.g., MIT) if planning to share publicly.

---
*Note: This project was originally developed in Spanish and the UI remains primarily in Spanish.*

----
Notas de los export de movimientos de cuentas:
- Bankinter: desde la web, excel importable
- Sabadell: desde la web, excel importable
- ING: desde la web, excel importable, con fecha en el name.
- OpenBank: desde la web, excel importable, sin fecha en el name, depdende de codigo movil
- CaixaBank: desde app movil, csv importable, con fecha en el name. (desde el web, excel no importable)
- Pluxee: desde la app movil, se envia al correo para descarga. Excel importable.
