# 📱 Plan de Implementación: Aplicación "Amazon Compras"

> 📌 **Nota preliminar:** Este documento es un **plan estratégico y procedimental**. No contiene fragmentos de código. Está diseñado para guiar el desarrollo de forma estructurada, escalable y alineada con las prácticas actuales de Flutter + Firebase (2024-2026).

---

## 🛠️ 1. Herramientas y Entorno de Desarrollo

| Categoría                 | Herramienta                                        | Propósito                                                  |
| ------------------------- | -------------------------------------------------- | ---------------------------------------------------------- |
| **IDE Principal**         | Visual Studio Code                                 | Desarrollo rápido, extensiones oficiales de Flutter/Dart   |
| **IDE Nativo (opcional)** | Android Studio / Xcode                             | Emuladores, firma de apps, depuración nativa               |
| **SDKs**                  | Flutter (canal estable) + Dart                     | Base del framework multiplataforma                         |
| **Control de Versiones**  | Git + GitHub/GitLab                                | Historial, colaboración, CI/CD                             |
| **Firebase**              | Firebase Console + Firebase CLI                    | Backend, autenticación, base de datos, despliegue          |
| **Diseño UI/UX**          | Figma / Penpot                                     | Wireframes, prototipos, design system, handoff             |
| **Gestión de Assets**     | SVG Repo, Flaticon, Unsplash                       | Iconografía, ilustraciones, imágenes de prueba             |
| **Pruebas**               | Flutter DevTools, Postman/Insomnia (Firebase REST) | Depuración, monitoreo de rendimiento, validación de reglas |

---

## 🎨 2. Diseño UI/UX

### 🔹 Fases de Diseño

1. **Investigación y Referencias:** Analizar flujos de Amazon, MercadoLibre y apps de e-commerce modernas.
2. **Arquitectura de Información:** Mapa de pantallas (Onboarding → Login → Home → Catálogo → Detalle → Carrito → Checkout → Perfil).
3. **Wireframes de Baja Fidelidad:** Definir disposición de elementos sin distracciones visuales.
4. **Design System:**

   * Paleta de colores (primario, secundario, estados, neutros)
   * Tipografía (tamaños, pesos, jerarquía)
   * Espaciado y grids (8pt base system)
   * Componentes reutilizables: botones, cards, inputs, skeletons, snackbars
5. **Prototipo Interactivo:** Validar navegación, transiciones y retroalimentación visual.
6. **Handoff a Desarrollo:** Exportar assets, tokens de diseño, especificaciones de layout y accesibilidad.

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

---

### 🌈 🔹 Uso de Degradados

Para lograr un diseño moderno y atractivo:

* **Header / AppBar premium:**
  Azul oscuro → Negro (#131921 → #000000)

* **Botones principales (CTA):**
  Naranja → Naranja claro (#FFA500 → #FFB84D)

* **Fondos suaves:**
  Gris claro → Blanco (#F2F2F2 → #FFFFFF)

👉 Estos degradados deben aplicarse en banners, botones principales y pantallas clave para generar profundidad visual.

---

### 🧩 🔹 Componentes Visuales Clave

* **Botones:**

  * Bordes redondeados (12px)
  * Color principal naranja
  * Sombra ligera
  * Animación al presionar

* **Cards de productos:**

  * Fondo blanco
  * Sombra suave (#0000000D)
  * Imagen + nombre + precio + rating
  * Botón de acción

* **AppBar:**

  * Color azul oscuro (#131921)
  * Íconos blancos
  * Barra de búsqueda integrada

* **Barra de búsqueda:**

  * Fondo blanco
  * Bordes redondeados
  * Icono gris

* **BottomNavigationBar:**

  * Activo: naranja
  * Inactivo: negro 54%

---

### 📐 🔹 Tipografía y Espaciado

* Sistema de espaciado: 8pt (8,16,24,32)
* Jerarquía:

  * Títulos: 20–24
  * Subtítulos: 16
  * Texto: 14
  * Precio: 18 (negrita)

---

### ✨ 🔹 Principios UX Aplicados

* **Ley de Fitts & Hick:** Minimizar clicks para acciones clave.
* **Feedback Inmediato:** Indicadores de carga, validaciones en tiempo real.
* **Accesibilidad:** Contraste adecuado y legibilidad.
* **Responsive/Adaptativo:** Compatible con móvil, tablet y web.
* **Microinteracciones:** Animaciones al agregar al carrito, transiciones suaves.

---

## 🔥 3. Configuración de Firebase

1. Crear proyecto en Firebase Console.
2. Registrar aplicaciones: Android, iOS y Web.
3. Configurar archivos de configuración nativos (`google-services.json`, `GoogleService-Info.plist`).
4. Habilitar **Authentication** → Método: Email/Password.
5. Crear base de datos **Firestore** en modo producción.

   * Colecciones alineadas a tu modelo:

     * `CLIENTE`, `PRODUCTO`, `PEDIDO`, `ITEM_PEDIDO`, `PAGO`, `ENVIO`, etc.
6. Configurar reglas de seguridad.
7. (Opcional) Configurar Storage para imágenes.

---

## 🏗️ 4. Arquitectura y Gestión de Estado

* **Patrón recomendado:** MVVM o Clean Architecture ligera.

* **Capas:**

  * `UI`: Widgets y pantallas con diseño visual aplicado (colores, degradados, sombras).
  * `Logic`: Providers.
  * `Data`: Firebase.
  * `Core`: Tema global (colores, estilos, tipografía).

* **Gestión de Estado:** `provider`

  * `AuthProvider`
  * `CartProvider`
  * `CatalogProvider`

* **Navegación:** `go_router`

---

## 📦 5. Dependencias Clave (`pubspec.yaml`)

*(Se mantiene igual, ya está correcto)*

---

## 📋 6. Procedimiento Paso a Paso (Fases de Desarrollo)

### 🟢 Fase 1: Configuración Inicial del Proyecto

* [ ] Crear proyecto Flutter
* [ ] Configurar Firebase
* [ ] Configurar dependencias

---

### 🟢 Fase 2: Esqueleto UI y Navegación Base

* [ ] Implementar tema global (incluyendo colores y degradados definidos)
* [ ] Crear AppBar estilo Amazon
* [ ] Crear navegación principal
* [ ] Implementar layout base con fondo gris claro
* [ ] Crear componentes reutilizables (botones, cards, searchbar)

---

### 🟢 Fase 3: Autenticación

* [ ] Pantallas de login modernas (minimalistas, fondo limpio)
* [ ] Validaciones visuales
* [ ] Manejo de sesión

---

### 🟢 Fase 4: Catálogo

* [ ] Cards de productos con diseño visual definido
* [ ] Uso de imágenes optimizadas
* [ ] Filtros y búsqueda

---

### 🟢 Fase 5: Carrito

* [ ] UI clara con lista de productos
* [ ] Total visible
* [ ] Botón de compra con degradado naranja

---

### 🟢 Fase 6: Checkout

* [ ] Selección de dirección (DIRECCION)
* [ ] Método de pago (METODO_PAGO)
* [ ] Confirmación visual atractiva

---

### 🟢 Fase 7: Pruebas y Despliegue

* [ ] Pruebas funcionales
* [ ] Optimización visual
* [ ] Publicación

---

## 🧾 🔹 Integración con tu Modelo de Datos

Las pantallas deben reflejar tus entidades:

| Entidad     | Uso en UI   |
| ----------- | ----------- |
| CLIENTE     | Perfil      |
| PRODUCTO    | Catálogo    |
| PEDIDO      | Historial   |
| ITEM_PEDIDO | Carrito     |
| PAGO        | Checkout    |
| ENVIO       | Seguimiento |
| RESEÑA      | Opiniones   |

---

## ✅ 7. Recomendaciones Finales y Buenas Prácticas

| Área              | Práctica                                  |
| ----------------- | ----------------------------------------- |
| **Diseño**        | Usar naranja solo en acciones importantes |
| **UX**            | No saturar la interfaz                    |
| **Rendimiento**   | Optimizar imágenes                        |
| **Código**        | Modular y limpio                          |
| **Escalabilidad** | Preparar para futuras funciones           |

---

## 🏁 Conclusión

Este plan integra tanto la estructura técnica como el diseño visual necesario para desarrollar una aplicación moderna tipo Amazon. La correcta aplicación de la paleta de colores, degradados y componentes visuales permitirá crear una experiencia atractiva, profesional y fácil de usar.

