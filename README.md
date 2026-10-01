# 🐾 Patitas Seguras - Chapitas Inteligentes (NFC + QR + Firebase)

Bienvenido a tu proyecto de chapitas inteligentes para mascotas. Este sistema permite que cualquier persona que encuentre a un perro extraviado escanee su código QR o acerque su teléfono con NFC para comunicarse de inmediato con su dueño. Además, incluye un apartado de venta directa para tu llavero **"patita"**.

---

## 📁 Archivos del Proyecto

```text
collar perro prototipo 1/
├── index.html    # Aplicación web completa (SPA, Tailwind CSS, Firebase v10)
└── README.md     # Este manual instructivo paso a paso
```

---

## ⚡ 1. Cómo Probarlo Inmediatamente en tu Computadora (Modo Demo)

La aplicación viene con un **modo demostración integrado**. Podés probarla ahora mismo sin configurar nada:
1. Hacé doble clic en el archivo [index.html](file:///C:/Users/thiag/Desktop/collar%20perro%20prototipo%201/index.html) para abrirlo en Chrome, Edge o tu navegador preferido.
2. Si lo abrís directamente, te pedirá que ingreses un código de prueba (ej: `perro-01`) o podés escribir en la barra de direcciones de tu navegador:
   ```text
   index.html?id=perro-01
   ```
3. Al ser un código nuevo, verás el **Formulario de Alta**. Completá los datos y tocá **"Guardar y Activar Chapita"**.
4. ¡Listo! Verás al instante la **Tarjeta de Rescate** con los botones de Llamada, WhatsApp, Ubicación y el bloque del llavero **"patita"**.

---

## 🔥 2. Cómo Configurar Firebase Firestore en Vivo (Paso a Paso)

Para que los datos se guarden en la nube y funcionen en cualquier celular del mundo:

### Paso 2.1: Crear el proyecto en Firebase
1. Ingresá a [Firebase Console](https://console.firebase.google.com/) con tu cuenta de Google.
2. Hacé clic en **"Crear un proyecto"** (o "Agregar proyecto").
3. Dale un nombre (ejemplo: `patitas-seguras`) y completá los pasos (podés desactivar Google Analytics si no lo necesitás).

### Paso 2.2: Crear la base de datos Firestore
1. En el menú lateral izquierdo, andá a **Compilación > Firestore Database**.
2. Hacé clic en **"Crear base de datos"**.
3. Elegí la ubicación más cercana (ej: `us-central` o `southamerica-east1`) y tocá **Siguiente**.
4. Seleccioná **"Comenzar en modo de prueba"** (para que permita lectura y escritura) y tocá **Habilitar**.

> **Reglas de seguridad recomendadas:**  
> En la pestaña **Reglas** de Firestore, asegurate de tener:
> ```javascript
> rules_version = '2';
> service cloud.firestore {
>   match /databases/{database}/documents {
>     match /pets/{petId} {
>       allow read, write: if true;
>     }
>   }
> }
> ```

### Paso 2.3: Obtener tus credenciales
1. Andá al icono de engranaje ⚙️ (arriba a la izquierda) > **Configuración del proyecto**.
2. En la sección **Tus apps**, hacé clic en el ícono web **`</>`**.
3. Registrá tu app con cualquier nombre (ej: `web-patitas`) y tocá **Registrar app**.
4. Copiá el bloque `const firebaseConfig = { ... }`.

### Paso 2.4: Pegar las credenciales en `index.html`
Abrí `index.html` con cualquier editor de texto o VS Code, buscá la línea 247 aproximadamente y reemplazá los valores:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "tu-proyecto.firebaseapp.com",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```
Guardá el archivo. ¡Firebase ya está conectado al 100%!

---

## 🐙 3. Cómo Subir el Proyecto a GitHub

1. Ingresá a [GitHub](https://github.com/) y creá un nuevo repositorio (por ejemplo: `collar-perro-patita`).
2. Marcalo como **Público**.
3. Podés subir los archivos de dos formas:
   * **Opción A (Fácil desde la web):** En la página de tu nuevo repositorio, hacé clic en **"uploading an existing file"**, arrastrá `index.html` y `README.md`, y hacé clic en **"Commit changes"**.
   * **Opción B (Por terminal de Git):**
     ```powershell
     cd "C:\Users\thiag\Desktop\collar perro prototipo 1"
     git init
     git add .
     git commit -m "Primer prototipo chapitas patitas"
     git branch -M main
     git remote add origin https://github.com/TU_USUARIO/collar-perro-patita.git
     git push -u origin main
     ```

---

## 🚀 4. Cómo Publicarlo Gratis en Netlify (En 2 Minutos)

1. Ingresá a [Netlify](https://www.netlify.com/) e iniciá sesión con tu cuenta de GitHub (o con correo).
2. Tenés dos métodos ultra rápidos:
   * **Método 1 (Arrastrar y Soltar - 10 segundos):**
     * En el panel de Netlify, andá a la pestaña **Sites**.
     * Tomá la carpeta entera `collar perro prototipo 1` desde tu escritorio y arrastrala directamente en el recuadro que dice *"Want to deploy a new site without connecting to Git? Drag and drop your site output folder here"*.
     * En 5 segundos tendrás tu enlace público (ej: `https://mi-patita-feliz.netlify.app`).
   * **Método 2 (Conectado a GitHub):**
     * Hacé clic en **"Add new site" > "Import an existing project"**.
     * Seleccioná **GitHub** y elegí tu repositorio `collar-perro-patita`.
     * Dejá las opciones predeterminadas y hacé clic en **Deploy**. Cada vez que modifiques código en GitHub, Netlify se actualizará solo.

---

## 🏷️ 5. Cómo Grabar los Tags NFC y Generar los Códigos QR

Una vez que tengas tu URL de Netlify (por ejemplo `https://mi-sitio.netlify.app`), cada chapita tendrá un identificador único en el enlace:

* Chapita 1: `https://mi-sitio.netlify.app/?id=PATITA-001`
* Chapita 2: `https://mi-sitio.netlify.app/?id=PATITA-002`
* Chapita 3: `https://mi-sitio.netlify.app/?id=PATITA-003`

### Para grabar el chip NFC:
1. Descargá en tu celular una app gratuita como **NFC Tools** (disponible para Android y iPhone).
2. Andá a **Escribir > Agregar un registro > URL / Enlace**.
3. Pegá la dirección de la chapita: `https://mi-sitio.netlify.app/?id=PATITA-001`.
4. Tocá **Escribir** y acercá la chapita al celular. ¡Queda grabada para siempre!

### Para el código QR:
1. Usá cualquier generador de QR gratuito (como [qr-code-generator.com](https://www.qr-code-generator.com/)).
2. Ingresá la misma URL (`https://mi-sitio.netlify.app/?id=PATITA-001`).
3. Descargá la imagen del QR para imprimirla o grabarla en el llavero.

---

## 💬 6. Sección de Venta del Llavero "patita"

El botón integrado en la web ya tiene configurado tu número y mensaje predeterminado:
* **Enlace configurado:** `https://wa.me/5491127979247?text=Hola,%20quiero%20mi%20patita`
* Quien visite la web y presione el botón verde de compra, te escribirá directamente a WhatsApp pidiéndote su llavero.
