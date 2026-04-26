📦 Foto Fast SpA — Panel de Gestión
Panel de gestión interno para Foto Fast SpA, negocio de insumos de oficina, papelería y embalaje. Construido como una Single Page Application (SPA) en HTML puro, conectada en tiempo real a Google Sheets como base de datos.


🚀 Demo
Desplegado automáticamente vía Vercel en cada push a main.


✨ Funcionalidades
Sección
Descripción
📊 Panel Principal
KPIs de ventas, compras, utilidad y resumen del mes actual
🏷️ Catálogo
Productos con costo, precio de venta, margen y filtros por categoría
👥 Clientes
Listado de clientes con acceso directo a WhatsApp
💰 Ventas
Registro y seguimiento de ventas con cálculo automático de IVA
📦 Compras
Registro de compras a proveedores
📅 Resumen Mensual
Tabla comparativa ventas vs compras por mes



🛠️ Stack Técnico
Frontend: HTML5 + CSS3 + JavaScript vanilla (sin frameworks)
Base de datos: Google Sheets (vía Google Visualization API)
Backend: Google Apps Script (para escritura de datos)
Deploy: Vercel (CD automático desde GitHub)
Fuentes: DM Serif Display + Plus Jakarta Sans (Google Fonts)


📁 Estructura del Proyecto
/

└── index.html       # App completa (SPA — un solo archivo)

└── README.md


⚙️ Configuración
La app se conecta a Google Sheets usando dos constantes definidas en el index.html:

const SHEET_ID = 'TU_SHEET_ID';

const API = 'TU_GOOGLE_APPS_SCRIPT_URL';
Google Sheets — Pestañas requeridas
El Sheets debe tener las siguientes pestañas con sus encabezados exactos:

Pestaña
Uso
Productos
Catálogo con SKU, nombre, categoría, unidad, costo y precio venta
Clientes
Datos de clientes (RUT, contacto, teléfono, email)
Proveedores
Datos de proveedores
Ventas
Registro de ventas emitidas
Compras
Registro de compras realizadas
ResumenMensual
Totales automáticos por mes (calculados por el Sheets)
Parametros
Tasa de IVA (por defecto 19%)

Google Apps Script
Para habilitar la escritura de datos (guardar ventas, compras y clientes), el Sheets debe tener un Apps Script desplegado como Web App con permisos públicos. La URL de ese script va en la constante API.


📱 Responsive
La app está optimizada para desktop y mobile:

Desktop: Sidebar fijo a la izquierda con navegación completa
Mobile: Top bar con menú hamburguesa + bottom navigation bar


🔄 Flujo de datos
Google Sheets  ──(Google Visualization API)──▶  Lectura en tiempo real

Google Sheets  ◀──(Google Apps Script POST)───  Escritura de registros

Los datos se cargan al iniciar la app y se pueden refrescar manualmente con el botón 🔄 Actualizar.


📦 Productos en Catálogo
Categorías disponibles:

Papel Fotocopia · Papel Especial · Bond Color · Cintas · Embalaje · Corchetes/Grapas · Dedales · Cuchillos Cartoneros · Equipos Oficina · Rollos Térmicos · Guantes · Kraft · Cajas · Paños/Limpieza


📄 Licencia
Uso privado — Foto Fast SpA. Todos los derechos reservados.

