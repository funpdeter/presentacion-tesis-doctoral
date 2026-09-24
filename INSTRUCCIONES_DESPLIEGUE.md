# 🚀 Guía de Despliegue a Producción en Dominio Web
## Presentación de Tesis Doctoral — Pontificia Universidad Javeriana
**Autor:** Rafael David Linero Ramos  
**Título:** *Fusión inteligente de información de múltiples sensores para evaluar la detección de enfermedades en cultivos de banano en el Departamento del Magdalena, Colombia*

---

Esta carpeta (`produccion_web/`) contiene **el paquete completo, optimizado y autosuficiente** para publicar la presentación en cualquier servidor web o vincularla a un dominio propio (`tudominio.com`).

---

## 📁 Estructura del Paquete de Producción

```text
produccion_web/
├── index.html                    <- Archivo principal (punto de entrada por defecto para la web)
├── presentacion_tesis.html       <- Copia directa para acceso por ruta específica
├── .htaccess                     <- Optimización Apache/cPanel (GZIP, caché y tipos MIME)
├── robots.txt                    <- Reglas para motores de búsqueda
├── INSTRUCCIONES_DESPLIEGUE.md   <- Este manual paso a paso
└── Presentation_Template_Javeriana/
    └── assets/
        ├── anime.min.js          <- Librería de animaciones (respaldo local offline)
        ├── javeriana_logo_blue_transparent.png     <- Escudo vertical Láminas 2-29
        ├── javeriana_logo_blue_horizontal.png      <- Logo horizontal azul Lámina 30
        ├── javeriana_logo_white_transparent.png     <- Escudo blanco Portada y Cierre
        └── [demás texturas e imágenes de soporte]
```

---

## 🌐 Opciones de Despliegue en la Web

### 🟢 Opción A: Vercel o Netlify (La más rápida y sencilla — Menos de 1 minuto)
Ambas plataformas ofrecen hosting ultrarrápido con CDN mundial, certificado SSL/HTTPS gratuito y soporte para dominios propios.

1. **Vercel (Recomendado):**
   * Ve a [vercel.com](https://vercel.com) e inicia sesión (con tu cuenta de GitHub, Google o email).
   * Haz clic en **"Add New..."** > **"Project"**.
   * Arrastra la carpeta completa `produccion_web` o el archivo `produccion_web.zip` a la ventana de Vercel.
   * Haz clic en **"Deploy"**. En 20 segundos tu presentación estará en línea con una URL segura (ej: `https://tesis-linero.vercel.app`).
   * Para conectar tu dominio propio: entra a *Settings* > *Domains* y añade tu dominio siguiendo las instrucciones de DNS (registro CNAME).

2. **Netlify:**
   * Ve a [netlify.com](https://netlify.com) e inicia sesión.
   * Ve a la sección **"Sites"** y arrastra la carpeta `produccion_web` en el área que dice *"Drag and drop your site output folder here"*.
   * ¡Listo! Te asignará una URL inmediata y en *Domain Management* podrás enlazar tu dominio propio.

---

### 🟢 Opción B: GitHub Pages (Gratuito, robusto y profesional)
Si utilizas un repositorio en GitHub:

1. Crea un repositorio en GitHub (ej: `tesis-doctoral`).
2. Sube todos los archivos y carpetas contenidos **dentro de `produccion_web/`** a la rama principal (`main`):
   ```bash
   cd produccion_web
   git init
   git add .
   git commit -m "Despliegue inicial de presentación tesis a producción"
   git branch -M main
   git remote add origin https://github.com/tu-usuario/tesis-doctoral.git
   git push -u origin main
   ```
3. En GitHub, ve a **Settings** > **Pages**.
4. En **Build and deployment** > **Source**, selecciona `Deploy from a branch` y escoge la rama `main` en la carpeta `/ (root)`. Guarda los cambios.
5. En 1 minuto tu presentación estará en `https://tu-usuario.github.io/tesis-doctoral/`.
6. Si tienes un dominio propio (ej: `tesis.tudominio.com`), en esa misma pantalla de configuración escríbelo en **Custom domain** y activa **Enforce HTTPS**.

---

### 🟢 Opción C: Hosting Tradicional con cPanel / Apache / Servidor Propio
Si tienes un servicio de hosting contratado con cPanel o acceso FTP:

1. Ingresa a tu **cPanel** > **Administrador de Archivos** (o conéctate por **FileZilla** vía SFTP/FTP).
2. Entra a la carpeta raíz de tu dominio (generalmente `public_html/` o un subdirectorio como `public_html/tesis/`).
3. Sube el contenido de `produccion_web` (asegúrate de que `index.html`, `.htaccess` y la carpeta `Presentation_Template_Javeriana` queden dentro de esa carpeta).
4. Si subes el archivo `produccion_web.zip`, puedes extraerlo directamente con la opción *Extract* de cPanel.
5. Al ingresar a tu dominio en el navegador (`https://tudominio.com/` o `https://tudominio.com/tesis/`), la presentación cargará automáticamente con compresión GZIP activa y caché optimizada.

---

## 💻 Prueba Local Previa (Sin conexión o antes de subir)
* Puedes abrir directamente el archivo `index.html` haciendo doble clic sobre él en tu explorador de archivos.
* O si deseas probarlo en un servidor local idéntico al de producción:
  ```powershell
  cd "c:\Users\ingra\OneDrive\Documents\1.TESIS\produccion_web"
  python -m http.server 8000
  ```
  Abre en tu navegador: `http://localhost:8000/`.
