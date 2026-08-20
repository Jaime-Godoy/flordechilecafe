# ☕ Flor de Chile Café — Sistema de Pedidos

Aplicación web de una sola página (single-file) para la toma de pedidos y gestión de comandas en cafetería. Pensada para uso en tablet o notebook, con una vista de **mesero/a** para tomar pedidos y una vista de **barista** para prepararlos.

## Índice

- [Características](#características)
- [Demo / Vista previa](#demo--vista-previa)
- [Cómo usar](#cómo-usar)
- [Flujo de trabajo](#flujo-de-trabajo)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Menú de productos](#menú-de-productos)
- [Tecnologías](#tecnologías)
- [Personalización](#personalización)
- [Limitaciones conocidas](#limitaciones-conocidas)
- [Roadmap](#roadmap)

## Características

- **Toma de pedidos rápida**: selección de ubicación (mesas, barra, para llevar) y menú de productos con precios.
- **Nombre del cliente (opcional)**: permite asociar un nombre a cada pedido para poder llamarlo cuando esté listo.
- **Carrito editable**: agrega o elimina ítems antes de enviar el pedido a preparación.
- **Panel de barista en tiempo real**: los pedidos enviados aparecen automáticamente como comandas.
- **Precio por comanda**: cada pedido pendiente muestra el detalle de precios por ítem y el total.
- **Historial de pedidos completados**: al marcar un pedido como "Listo", pasa a una pestaña de historial con hora de ingreso, hora de finalización y total.
- **Contador de pedidos pendientes** visible en el encabezado del panel de barista.
- **Sin backend ni dependencias de instalación**: todo corre en un único archivo HTML.

## Demo / Vista previa

La interfaz se divide en dos columnas:

| Sección | Descripción |
|---|---|
| **Toma de Pedidos** (2/3 de la pantalla) | Selección de ubicación, grilla de productos y carrito de compra actual. |
| **Comandas (Barista)** (1/3 de la pantalla) | Pestañas de "Pendientes" e "Historial" con las comandas a preparar. |

## Cómo usar

1. Descarga el archivo [`barista.html`](./barista.html).
2. Ábrelo directamente en cualquier navegador moderno (Chrome, Edge, Firefox, Safari) haciendo doble clic, o sírvelo desde un servidor estático (por ejemplo, GitHub Pages).
3. No requiere instalación, build ni servidor backend.

```bash
# Opción rápida: abrir localmente
open barista.html        # macOS
start barista.html       # Windows
xdg-open barista.html    # Linux
```

## Flujo de trabajo

1. **Seleccionar ubicación**: elige Mesa 1, Mesa 2, Mesa 3, Barra o Para Llevar.
2. **Ingresar nombre del cliente** *(opcional)*: escribe el nombre en el campo correspondiente para poder llamarlo cuando su pedido esté listo.
3. **Agregar productos**: toca cualquier producto del menú para añadirlo al carrito. Se puede repetir el mismo producto varias veces.
4. **Revisar el pedido**: en la sección "Orden Actual" se puede eliminar cualquier ítem con el botón `×`.
5. **Enviar a preparación**: al presionar el botón, el pedido se envía al panel de barista y el carrito (junto con el nombre del cliente) se limpia para el siguiente cliente.
6. **Preparar y completar**: en el panel de barista, cada comanda muestra el nombre del cliente (si se ingresó), los ítems, sus precios y el total. Al presionar **"Listo ✓"**, el pedido se mueve automáticamente a la pestaña **Historial**.
7. **Consultar historial**: la pestaña "Historial" lista los pedidos completados (más recientes primero), con nombre del cliente, hora de ingreso, hora de entrega y total.

> ⚠️ El sistema exige seleccionar una ubicación antes de enviar el pedido; si no se hace, se muestra una advertencia.

## Estructura del proyecto

```
.
└── barista.html   # Aplicación completa (HTML + Tailwind CDN + JavaScript vanilla)
```

Todo el código —marcado, estilos y lógica— vive en un único archivo, sin dependencias externas más allá del CDN de Tailwind CSS.

## Menú de productos

### Cafetería

| Producto | Precio |
|---|---|
| Expresso | $1.900 |
| Expresso Doble | $2.500 |
| Americano | $2.000 |
| Capuccino | $2.200 |
| Capuccino + Sabor | $2.500 |
| Chai Latte | $1.400 |
| Chocolate Caliente | $1.600 |

### Comida y bebidas

| Producto | Precio |
|---|---|
| Sopaipilla (1) | $350 |
| Promo 3 Sopaipillas | $1.000 |
| Paquete Galletas | $1.000 |
| Jugo en Caja | $600 |
| Jugo en Botella | $1.300 |

## Tecnologías

- **HTML5**
- **[Tailwind CSS](https://tailwindcss.com/)** vía CDN (`cdn.tailwindcss.com`)
- **JavaScript vanilla** (sin frameworks ni build tools)

## Personalización

- **Colores**: definidos en la configuración de Tailwind dentro del `<head>` (`cafe`, `crema`, `acento`). Modifica esos valores hexadecimales para cambiar la paleta.
- **Productos y precios**: se agregan/editan directamente en la sección `<!-- Productos -->`, agregando botones con `onclick="agregarAlCarrito('Nombre', precio)"`.
- **Ubicaciones**: se agregan nuevos botones en `#botones-ubicacion` con `onclick="seleccionarUbicacion('Nombre')"`.

## Limitaciones conocidas

- **Sin persistencia**: todo el estado (pedidos, historial) vive en memoria del navegador. Al recargar la página se pierde toda la información.
- **Sin sincronización multi-dispositivo**: si se abre en dos pestañas o dispositivos distintos, cada uno mantiene su propio estado independiente.
- **Sin autenticación**: cualquier persona con acceso al archivo puede tomar pedidos o marcar comandas como completadas.

## Roadmap

Ideas para futuras versiones:

- [ ] Persistencia local (localStorage) o backend real con base de datos.
- [ ] Reportes de ventas por día/turno.
- [ ] Edición de cantidades por ítem (en vez de repetir el producto).
- [ ] Notas/observaciones por pedido (ej. "sin azúcar", "para llevar en 2 vasos").
- [ ] Impresión de comandas para cocina/barra.

---

Hecho con ❤️ para **Flor de Chile Café**.
