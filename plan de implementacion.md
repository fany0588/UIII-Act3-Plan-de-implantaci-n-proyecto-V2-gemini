
# 📱 PLAN DE IMPLEMENTACIÓN PROFESIONAL

## Aplicación “Amazon Compras”

> 📌 **Documento técnico de arquitectura y desarrollo**
> Este documento define la planificación completa para el desarrollo de una aplicación de comercio electrónico multiplataforma tipo Amazon, utilizando tecnologías modernas de desarrollo móvil y web. Está diseñado bajo estándares de escalabilidad, mantenibilidad y buenas prácticas de ingeniería de software (2024–2026).

---

# 🧠 1. VISIÓN GENERAL DEL SISTEMA

La aplicación “Amazon Compras” es una plataforma de comercio electrónico que permite a los usuarios registrarse, explorar productos, gestionar un carrito de compras, realizar pedidos y seguir envíos en tiempo real.

El sistema estará construido con:

* Framework principal: **Flutter (Dart)**
* Backend en la nube: **Firebase**
* Base de datos: **Cloud Firestore**
* Estado global: **Provider**
* Diseño UI/UX: **Antigravity + Figma**

---

# 🛠️ 2. TECNOLOGÍAS Y ENTORNO DE DESARROLLO

| Categoría            | Tecnología          | Descripción                |
| -------------------- | ------------------- | -------------------------- |
| Framework            | Flutter             | Desarrollo multiplataforma |
| Lenguaje             | Dart                | Lenguaje principal         |
| Backend              | Firebase            | Servicios en la nube       |
| Base de datos        | Firestore           | NoSQL escalable            |
| Autenticación        | Firebase Auth       | Email y contraseña         |
| Estado               | Provider            | Gestión global de estado   |
| Diseño UI            | Antigravity + Figma | Diseño visual              |
| Control de versiones | Git + GitHub        | Versionado del proyecto    |

---

## 📱 2.1 PLATAFORMAS OBJETIVO

* Android 📱
* iOS 🍎
* Web 🌐
* Windows 🖥️

---

# ⚙️ 3. CONFIGURACIÓN DEL SISTEMA

## 🔐 3.1 Autenticación

* Método obligatorio: **Correo electrónico + contraseña**
* Recuperación de contraseña habilitada
* Persistencia de sesión activa
* Validación de seguridad de contraseña

---

## ☁️ 3.2 BASE DE DATOS

* Plataforma: Firebase Console
* Motor: Cloud Firestore
* Estructura NoSQL basada en colecciones

### ❌ Restricciones del sistema:

* No se utilizará Firebase Analytics
* No se utilizará tracking de producción

---

# 🎨 4. DISEÑO UI / UX PROFESIONAL

## 🎯 4.1 ENFOQUE DE DISEÑO

El diseño se basa en principios de:

* Minimalismo funcional
* Jerarquía visual clara
* Experiencia tipo Amazon
* Optimización de conversión (UX de compra)

---

### 🎨 🔹 Paleta de Colores (Estilo Amazon)

| Uso                | Color       | HEX       |
| ------------------ | ----------- | --------- |
| 🔵 Principal       | Azul oscuro | #131921   |
| ⚪ Fondo            | Gris claro  | #F2F2F2   |
| ⚪ Cards            | Blanco      | #FFFFFF   |
| 🟠 Acento          | Naranja     | #FFA500   |
| ⚫ Texto            | Negro       | #000000   |
| ⚫ Texto secundario | Negro 54%   | #0000008A |
| ⚫ Sombra fuerte    | Negro 12%   | #0000001F |
| ⚫ Sombra ligera    | Negro 5%    | #0000000D |
| ⚪ Overlay          | Blanco 70%  | #FFFFFFB3 |
| ⚫ Bordes           | Gris        | #9E9E9E   |
| 🔍 Transparente    | -           | #00000000 |

--

## 🌈 4.3 SISTEMA DE DEGRADADOS

* Header principal: `#131921 → #000000`
* Botones CTA: `#FFA500 → #FFB84D`
* Fondos suaves: `#F2F2F2 → #FFFFFF`

👉 Aplicación en:

* AppBar
* Banners promocionales
* Botones principales
* Pantallas de checkout

---

## 🧩 4.4 SISTEMA DE COMPONENTES UI

### 🔝 AppBar

* Color sólido o degradado oscuro
* Barra de búsqueda integrada
* Iconos blancos

---

### 🛒 Cards de producto

* Imagen optimizada
* Nombre del producto
* Precio destacado
* Rating con estrellas
* Botón “Agregar al carrito”

---

### 🔘 Botones

* Bordes redondeados (12px)
* Animación de presión
* Sombra suave
* Estado activo/inactivo

---

### 🔎 Barra de búsqueda

* Fondo blanco
* Bordes redondeados
* Placeholder dinámico
* Icono de búsqueda gris

---

### 🧭 Navegación inferior

* BottomNavigationBar
* Estado activo naranja
* Estado inactivo gris

---

## 📐 4.5 SISTEMA TIPOGRÁFICO

| Elemento  | Tamaño       |
| --------- | ------------ |
| Título    | 24 px        |
| Subtítulo | 16 px        |
| Texto     | 14 px        |
| Precio    | 18 px (bold) |

---

## ✨ 4.6 EXPERIENCIA DE USUARIO (UX)

* Microinteracciones fluidas
* Feedback inmediato
* Estados vacíos diseñados
* Animaciones suaves
* Reducción de fricción en compra

---

# 🧠 5. USO DE ANTIGRAVITY

Antigravity será utilizado como herramienta de diseño visual para:

* Construcción de interfaces sin código
* Prototipado rápido de pantallas
* Exportación de layouts a Flutter
* Definición de componentes reutilizables

---

## 🔄 Flujo de trabajo

1. Diseño UI en Antigravity
2. Exportación visual
3. Implementación en Flutter
4. Conexión con Provider + Firebase

---

# 🏗️ 6. ARQUITECTURA DEL SISTEMA

## 📌 Patrón arquitectónico

* MVVM (Model - View - ViewModel)
* Provider como gestor de estado

---

## 📦 CAPAS DEL SISTEMA

### 🎨 UI Layer

* Pantallas Flutter
* Widgets reutilizables
* Diseño visual

### 🧠 Logic Layer

* Provider
* Validaciones
* Estado global

### ☁️ Data Layer

* Firebase
* Firestore
* Auth

### 🧱 Core Layer

* Tema global
* Constantes
* Rutas
* Configuración

---

# 📁 7. ESTRUCTURA DE CARPETAS (FLUTTER)

```plaintext
lib/
│
├── core/
│   ├── theme/
│   ├── constants/
│   ├── routes/
│   ├── utils/
│
├── data/
│   ├── models/
│   ├── services/
│   ├── repositories/
│
├── provider/
│   ├── auth_provider.dart
│   ├── cart_provider.dart
│   ├── product_provider.dart
│
├── ui/
│   ├── screens/
│   │   ├── auth/
│   │   ├── home/
│   │   ├── product/
│   │   ├── cart/
│   │   ├── checkout/
│   │
│   ├── widgets/
│
├── main.dart
```

---

# 📦 8. DEPENDENCIAS DEL PROYECTO

```yaml
dependencies:
  flutter:
    sdk: flutter

  provider: ^latest
  firebase_core: ^latest
  firebase_auth: ^latest
  cloud_firestore: ^latest

  go_router: ^latest
  cached_network_image: ^latest
  shared_preferences: ^latest
  intl: ^latest
  uuid: ^latest
```


---

# 🧾 9. MODELO DE DATOS (ENTIDADES)

## 👤 CLIENTE

| Campo         | Tipo    | Descripción                     |
| ------------- | ------- | ------------------------------- |
| id_cliente    | PK      | Identificador único del cliente |
| nombre        | String  | Nombre completo del cliente     |
| email         | String  | Correo electrónico (login)      |
| password      | String  | Contraseña encriptada           |
| estado_cuenta | Boolean | Estado activo/inactivo          |

---

## 🏠 DIRECCIÓN

| Campo         | Tipo   | Descripción                |
| ------------- | ------ | -------------------------- |
| id_direccion  | PK     | Identificador de dirección |
| id_cliente    | FK     | Relación con CLIENTE       |
| calle         | String | Calle y número             |
| ciudad        | String | Ciudad                     |
| codigo_postal | String | Código postal              |

---

## 💳 MÉTODO DE PAGO

| Campo          | Tipo   | Descripción                            |
| -------------- | ------ | -------------------------------------- |
| id_pago        | PK     | Identificador del método de pago       |
| id_cliente     | FK     | Cliente propietario                    |
| tipo           | String | Tipo de pago (tarjeta, efectivo, etc.) |
| numero_tarjeta | String | Número encriptado de tarjeta           |

---

## 📦 PRODUCTO

| Campo        | Tipo    | Descripción                |
| ------------ | ------- | -------------------------- |
| id_producto  | PK      | Identificador del producto |
| nombre       | String  | Nombre del producto        |
| descripcion  | String  | Detalles del producto      |
| precio       | Double  | Precio actual              |
| stock        | Integer | Cantidad disponible        |
| imagen       | String  | URL de imagen              |
| id_categoria | FK      | Categoría del producto     |

---

## 🗂️ CATEGORÍA

| Campo        | Tipo          | Descripción                  |
| ------------ | ------------- | ---------------------------- |
| id_categoria | PK            | Identificador de categoría   |
| nombre       | String        | Nombre de categoría          |
| padre_id     | FK (nullable) | Subcategoría (auto-relación) |

---

## 🛒 PEDIDO

| Campo      | Tipo   | Descripción                            |
| ---------- | ------ | -------------------------------------- |
| id_pedido  | PK     | Identificador del pedido               |
| id_cliente | FK     | Cliente que realiza la compra          |
| total      | Double | Monto total del pedido                 |
| estado     | String | Estado (pendiente, enviado, entregado) |

---

## 📦 ITEM_PEDIDO

| Campo           | Tipo    | Descripción                    |
| --------------- | ------- | ------------------------------ |
| id_item         | PK      | Identificador del item         |
| id_pedido       | FK      | Pedido relacionado             |
| id_producto     | FK      | Producto comprado              |
| cantidad        | Integer | Cantidad del producto          |
| precio_unitario | Double  | Precio en el momento de compra |

---

## 💳 PAGO

| Campo     | Tipo   | Descripción            |
| --------- | ------ | ---------------------- |
| id_pago   | PK     | Identificador del pago |
| id_pedido | FK     | Pedido asociado        |
| metodo    | String | Método de pago         |
| estado    | String | Estado del pago        |

---

## 🚚 ENVÍO

| Campo         | Tipo   | Descripción             |
| ------------- | ------ | ----------------------- |
| id_envio      | PK     | Identificador del envío |
| id_pedido     | FK     | Pedido relacionado      |
| transportista | String | Empresa de envío        |
| estado        | String | Estado del envío        |
| guia          | String | Número de rastreo       |

---

## 🚛 TRANSPORTISTA

| Campo            | Tipo   | Descripción                     |
| ---------------- | ------ | ------------------------------- |
| id_transportista | PK     | Identificador del transportista |
| nombre           | String | Nombre de la empresa            |

---

## ⭐ RESEÑA

| Campo        | Tipo    | Descripción             |
| ------------ | ------- | ----------------------- |
| id_resena    | PK      | Identificador de reseña |
| id_producto  | FK      | Producto evaluado       |
| id_cliente   | FK      | Cliente que opina       |
| comentario   | String  | Texto de la reseña      |
| calificacion | Integer | Puntuación (1–5)        |

---


# 🔄 10. FLUJO DE LA APLICACIÓN

1. Splash Screen
2. Login / Registro
3. Home (Catálogo)
4. Detalle de producto
5. Carrito
6. Checkout
7. Confirmación de pedido

---


# 📋 11. FASES DE DESARROLLO

## 🟢 Fase 1: Configuración del Proyecto

### 🎯 Objetivo

Establecer el entorno base de desarrollo y la estructura inicial del sistema.

### ⚙️ Actividades

* Configuración del proyecto en **Flutter**
* Integración inicial con **Firebase**
* Configuración de dependencias principales
* Creación de estructura base de carpetas
* Configuración de control de versiones con Git

### 📦 Resultado

Proyecto funcional con arquitectura base lista para desarrollo.

---

## 🟢 Fase 2: Diseño UI/UX

### 🎯 Objetivo

Definir y construir la identidad visual del sistema.

### 🎨 Actividades

* Diseño de interfaces en **Antigravity**
* Creación del sistema de diseño (Design System)
* Definición de paleta de colores y tipografía
* Diseño de componentes reutilizables (botones, cards, inputs)
* Implementación del tema global en Flutter

### 📦 Resultado

Sistema visual consistente y reutilizable en toda la aplicación.

---

## 🟢 Fase 3: Autenticación de Usuarios

### 🎯 Objetivo

Implementar el sistema de acceso seguro a la aplicación.

### 🔐 Actividades

* Login con correo electrónico y contraseña
* Registro de usuarios
* Recuperación de contraseña
* Validaciones de formularios
* Integración con **Firebase Authentication**
* Gestión de sesión con **Provider**

### 📦 Resultado

Sistema de autenticación funcional, seguro y persistente.

---

## 🟢 Fase 4: Módulo de Catálogo

### 🎯 Objetivo

Desarrollar el sistema de visualización de productos.

### 📦 Actividades

* Listado de productos desde Firestore
* Diseño de tarjetas de producto
* Detalle de producto
* Filtros por categoría
* Búsqueda de productos
* Integración con modelo de datos PRODUCTO y CATEGORIA

### 📦 Resultado

Catálogo dinámico y conectado a base de datos.

---

## 🟢 Fase 5: Carrito de Compras

### 🎯 Objetivo

Permitir la gestión de productos seleccionados por el usuario.

### 🛒 Actividades

* Agregar productos al carrito
* Eliminar productos
* Modificar cantidades
* Cálculo de totales en tiempo real
* Gestión de estado con **Provider (CartProvider)**
* Persistencia de datos temporal

### 📦 Resultado

Sistema de carrito funcional y dinámico.

---

## 🟢 Fase 6: Checkout y Pagos

### 🎯 Objetivo

Implementar el flujo completo de compra.

### 💳 Actividades

* Selección de dirección de envío
* Selección de método de pago
* Confirmación de pedido
* Creación de registros en PEDIDO, PAGO e ITEM_PEDIDO
* Generación de orden final
* Pantalla de éxito de compra

### 📦 Resultado

Flujo completo de compra operativo.

---

## 🟢 Fase 7: Pruebas y Optimización

### 🎯 Objetivo

Garantizar el correcto funcionamiento y rendimiento del sistema.

### 🧪 Actividades

* Pruebas funcionales de todas las pantallas
* Validación de flujos de usuario
* Optimización de rendimiento en Flutter
* Corrección de errores
* Revisión de UI/UX
* Ajustes de seguridad en Firebase

### 📦 Resultado

Aplicación estable, optimizada y lista para despliegue.

---


# 🏁 12. CONCLUSIÓN

Este plan define una arquitectura completa, escalable y profesional para el desarrollo de una aplicación tipo Amazon utilizando Flutter, Firebase y Provider, integrando un diseño UI/UX moderno basado en una paleta de colores optimizada, degradados, componentes reutilizables y una estructura de datos robusta.

---
## PROMPT
Actúa como un arquitecto de software y diseñador UI/UX experto en Flutter, y genera un documento técnico completo para una aplicación multiplataforma de comercio electrónico llamada “Amazon Compras”.

El sistema debe desarrollarse con Flutter (Dart) como framework principal, Firebase como backend, Cloud Firestore como base de datos y Firebase Authentication para login y registro con correo electrónico y contraseña. No debe incluir Firebase Analytics ni herramientas de tracking en producción.

La aplicación debe ser compatible con Android, iOS, Web y Windows, utilizando una arquitectura MVVM con Provider para gestión de estado, organizada en capas: UI, Logic, Data y Core, con una estructura de carpetas profesional en Flutter.

El diseño UI/UX debe basarse en un sistema moderno tipo Amazon, utilizando Antigravity como herramienta principal de diseño, con una paleta de colores definida:

Azul oscuro: #131921
Gris claro: #F2F2F2
Blanco: #FFFFFF
Negro: #000000
Naranja: #FFA500
Tonos de sombra y transparencia (variantes en negro y blanco)

Se deben incluir degradados profesionales en headers (#131921 → #000000), botones (#FFA500 → #FFB84D) y fondos (#F2F2F2 → #FFFFFF), además de componentes como AppBar con buscador, BottomNavigationBar, cards de productos, carrito, checkout y animaciones de interacción.

El modelo de datos debe incluir las entidades: CLIENTE, DIRECCION, METODO_PAGO, PRODUCTO, CATEGORIA, PEDIDO, ITEM_PEDIDO, PAGO, ENVIO, TRANSPORTISTA y RESEÑA, con atributos bien definidos para gestión de usuarios, productos, pagos y logística.

El flujo de la aplicación debe contemplar: splash, login/registro, catálogo, detalle de producto, carrito, checkout, confirmación y seguimiento de pedidos.

El desarrollo debe dividirse en 7 fases: configuración, diseño UI/UX, autenticación, catálogo, carrito, checkout y pruebas.

El resultado esperado es una aplicación escalable, moderna y profesional tipo Amazon, con arquitectura limpia, UI/UX optimizado y backend en Firebase listo para producción.
