
# 📦  Plan: E-Commerce "Amazon Compras"

### *Estrategia de Desarrollo y Arquitectura de Datos 2026*

---

## 🎨 1. Sistema de Diseño (Visual Identity)

Para que la aplicación se vea **increíble**, no basta con los colores; necesitamos aplicarlos con la técnica de **60-30-10** (60% fondo neutro, 30% primario, 10% acento).

### 🏷️ Definición de Tokens de Color

| Elemento | Color | HEX | Implementación UI |
| --- | --- | --- | --- |
| **Primario** | Azul Amazon | `#131921` | AppBar, BottomNav y Headers. |
| **Acento** | Naranja Amazon | `#FFA500` | Botones "Call to Action" y Ratings. |
| **Fondo** | Gris Light | `#F2F2F2` | Fondo de los Scaffolds para contraste. |
| **Superficie** | Pure White | `#FFFFFF` | Cards de productos y campos de texto. |
| **Desactivado** | Negro 54% | `#0000008A` | Iconos de estado inactivo. |

### ✨ Estética Avanzada

* **Degradados de Marca:** En el encabezado, usa un `LinearGradient` de `#131921` a `#232F3E` con un ángulo de 180°.
* **Micro-interacciones:** Al presionar el botón naranja (`#FFA500`), el widget debe escalar un 5% (`transform: scale(0.95)`) para dar feedback táctil.
* **Sombras:** Evita bordes negros. Usa `box-shadow: 0 4px 12px rgba(0,0,0,0.12)` para las tarjetas de producto.

---

## 🗄️ 2. Arquitectura de Datos Administrada

Como administrador de datos, hemos organizado la información en **4 Dominios de Dominancia Relacional**. Esto garantiza que la app pueda escalar de 100 a 1,000,000 de productos sin romperse.

### 🏗️ Diccionario de Entidades (12 Tablas)

| Dominio | Entidades | Relación Clave |
| --- | --- | --- |
| **Usuarios** | `CLIENTE`, `DIRECCION`, `METODO_PAGO` | Un Cliente → Varias Direcciones (1:N). |
| **Catálogo** | `PRODUCTO`, `CATEGORIA`, `VENDEDOR` | Un Vendedor → Varios Productos (1:N). |
| **Ventas** | `PEDIDO`, `ITEM_PEDIDO`, `PAGO` | Un Pedido → Muchos Items (1:N). |
| **Logística** | `ENVIO`, `TRANSPORTISTA`, `RESENA` | Un Pedido → Un Envío (1:1). |

---

## 🛠️ 3. Stack Tecnológico y Configuración

| Capa | Tecnología | Implementación |
| --- | --- | --- |
| **Frontend** | Flutter SDK 3.x | Widgets reactivos y compilación nativa. |
| **Base de Datos** | Cloud Firestore | Sincronización en tiempo real para stock y chats. |
| **Autenticación** | Firebase Auth | OAuth, Email y persistencia de token. |
| **Archivos** | Firebase Storage | Hosting de imágenes optimizadas para WebP. |

---

## 📋 4. Procedimiento de Ejecución (Fases de Desarrollo)

### 🟢 Fase 1: Estructura y Theme Data

* [ ] Configurar `MaterialApp` con un `ThemeData` personalizado.
* [ ] Definir los colores HEX en una clase de constantes `AppColors`.
* [ ] Implementar el `Skeleton Loader` (Placeholder) con el color `#0000000D`.

### 🔵 Fase 2: Motor de Catálogo

* [ ] Implementar la entidad `CATEGORIA` con soporte para sub-categorías (jerarquía).
* [ ] Crear el widget de `ProductCard` con bordes redondeados (8.0) y elevación suave.
* [ ] Integrar `cached_network_image` para persistencia visual sin conexión.

### 🟡 Fase 3: Lógica de Transacción

* [ ] **CartProvider:** Lógica de cálculo (Precio x Cantidad) + Gastos de Envío.
* [ ] **Snapshot de Seguridad:** Copiar los datos del `PRODUCTO` a `ITEM_PEDIDO` para evitar que cambios de precio futuros afecten órdenes pasadas.

### 🔴 Fase 4: Checkout y Tracking

* [ ] Flujo de 3 pasos: Dirección → Pago → Confirmación.
* [ ] Integración de la entidad `ENVIO` para mostrar la barra de progreso al cliente.

---

## 📜 5. Script de Inicialización (bdamazon.sql)

Este script prepara tu entorno SQL para pruebas de consistencia de datos antes de pasar a la nube de Firebase.

```sql
/* BDAMAZON - Script de Estructura Profesional 
   Entities: 12 | Relational Integrity: Active
*/

CREATE DATABASE bdamazon;
USE bdamazon;

-- 1. Gestión de Usuarios
CREATE TABLE CLIENTE (
    id_cliente INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 2. Gestión de Catálogo
CREATE TABLE VENDEDOR (
    id_vendedor INT PRIMARY KEY AUTO_INCREMENT,
    nombre_tienda VARCHAR(100) NOT NULL,
    rating DECIMAL(2,1) DEFAULT 0.0
);

CREATE TABLE PRODUCTO (
    id_producto INT PRIMARY KEY AUTO_INCREMENT,
    id_vendedor INT,
    nombre VARCHAR(255) NOT NULL,
    precio DECIMAL(10,2) NOT NULL,
    stock INT DEFAULT 0,
    FOREIGN KEY (id_vendedor) REFERENCES VENDEDOR(id_vendedor)
);

-- 3. Gestión de Pedidos (Snapshot de precios)
CREATE TABLE PEDIDO (
    id_pedido INT PRIMARY KEY AUTO_INCREMENT,
    id_cliente INT,
    total DECIMAL(10,2),
    estado VARCHAR(50) DEFAULT 'Procesando',
    FOREIGN KEY (id_cliente) REFERENCES CLIENTE(id_cliente)
);

CREATE TABLE ITEM_PEDIDO (
    id_item INT PRIMARY KEY AUTO_INCREMENT,
    id_pedido INT,
    id_producto INT,
    cantidad INT,
    precio_historico DECIMAL(10,2), -- Precio al momento de compra
    FOREIGN KEY (id_pedido) REFERENCES PEDIDO(id_pedido)
);

-- [Tablas adicionales de ENVIO, PAGO, RESENA y DIRECCION según arquitectura]

```

---

## ✅ 6. Recomendaciones de "Admin de Datos"

1. **Integridad Referencial:** En Firebase, nunca borres un producto si ya tiene pedidos asociados. Cambia su estado a `is_active: false`.
2. **Caché Local:** Usa `shared_preferences` para guardar el nombre del usuario y su última categoría vista, logrando que la app inicie en menos de 1 segundo.
3. **UI Increíble:** Asegúrate de que el botón de **"Comprar Ahora"** sea el único elemento con el color naranja vibrante en la pantalla de detalle para maximizar la conversión.

