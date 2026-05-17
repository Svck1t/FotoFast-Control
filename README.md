# Foto Fast SpA — Sistema de Gestión

Sistema web interno de **Foto Fast SpA** (insumos de oficina, papelería y embalaje — Cerro Navia, Santiago) para cotizar, registrar ventas y compras, administrar clientes y llevar el control comercial del negocio.

Aplicación de una sola página (SPA), sin framework ni proceso de build: todo vive en un único archivo `index.html`.

🔗 **Producción:** https://foto-fast-control.vercel.app

---

## Funcionalidades

El sistema se organiza en 7 módulos accesibles desde el menú lateral:

| Módulo | Qué hace |
|---|---|
| **Panel** | Tablero con indicadores clave del negocio (cobros pendientes, resumen de actividad). |
| **Catálogo** | Listado de productos con precios, buscador integrado. |
| **Cotizar** | Crea cotizaciones, genera el PDF, las comparte por WhatsApp y guarda el historial. |
| **Clientes** | Administra clientes con estados (prospecto · activo · inactivo). |
| **Ventas** | Registra ventas con seguimiento de cobro (Pendiente · Pagado · Parcial · Anulado). |
| **Compras** | Registra compras a proveedores. |
| **Resumen** | Vista consolidada del estado financiero. |

### Cotizaciones

- Numeración secuencial automática con formato `FF-AAAA-NNN`.
- PDF tamaño A4 con encabezado corporativo, logo, datos del cliente, detalle de productos y totales (Neto · IVA 19% · Total).
- Tabla del PDF de 3 columnas: **Producto / Descripción · Precio C/U · Cantidad**.
- Validez configurable (por defecto 30 días).
- Botón para compartir la cotización directamente por WhatsApp.
- Estados con código de color: `Borrador` · `Enviada` · `Aprobada` · `Pendiente` · `Pagada` · `Cobro Parcial` · `Rechazada`.

### Diseño responsive

- **Escritorio:** menú lateral fijo.
- **Móvil:** barra de navegación inferior + menú hamburguesa en la barra superior.

---

## Arquitectura

| Capa | Tecnología |
|---|---|
| Frontend | HTML + CSS + JavaScript (sin framework) |
| Generación de PDF | [jsPDF 2.5.1](https://github.com/parallax/jsPDF) vía CDN |
| Persistencia local | `localStorage` (historial de cotizaciones y contador correlativo) |
| Backend / base de datos | Google Apps Script (Web App) que escribe en Google Sheets |
| Hosting | Vercel |
| Repositorio | GitHub |

### Datos almacenados localmente

- `ff_cotizaciones` — historial de cotizaciones.
- `ff_cot_counter` — contador para la numeración correlativa.

### Sincronización con Google Sheets

El sistema envía ventas, compras y registros a una **Web App de Google Apps Script** (constante `API` en `index.html`), que los vuelca a la planilla de Google Sheets. El estado de la sincronización se muestra en el pie del menú lateral.

> ⚠️ La URL de la Web App de Apps Script está en la constante `API` dentro de `index.html`. Si se regenera el despliegue de Apps Script, hay que actualizar ese valor.

---

## Despliegue

El flujo de actualización es manual y directo:

1. Editar `index.html`.
2. Subir el archivo actualizado a este repositorio en GitHub.
3. Vercel detecta el cambio y publica automáticamente la nueva versión.

No requiere instalación de dependencias ni paso de compilación.

---

## Configuración inicial (clonar el sistema en otro entorno)

1. Crear la planilla de Google Sheets con las hojas correspondientes.
2. Publicar el Apps Script asociado como **Web App** y copiar su URL `/exec`.
3. Reemplazar el valor de la constante `API` en `index.html` con esa URL.
4. Subir `index.html` al repositorio y conectar el repo a Vercel.

---

## Changelog

### Mayo 2026
- Logo actualizado a la versión con **fondo blanco**, tanto en el menú lateral como en el encabezado del PDF de cotización.
- Eliminada la columna **Subtotal** del PDF de cotización: la tabla pasó a 3 columnas (Producto · Precio C/U · Cantidad) para una presentación más limpia. Los totales (Neto · IVA · Total) se mantienen al pie.

---

## Contacto

**Foto Fast SpA**
📧 fotofast.cl@gmail.com
📱 WhatsApp Business: +56 9 8736 4530 · +56 9 5491 1225
📍 Cerro Navia, Santiago, Chile
