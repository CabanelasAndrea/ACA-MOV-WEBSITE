# ACA MOVILIDAD - Sitio Web Administrable

## 🚀 Versión con Netlify CMS

Este es el sitio web de ACA MOVILIDAD con un **panel de administración** que te permite editar todo el contenido sin saber código.

## 📋 ¿Qué incluye?

- ✅ **Panel de Admin** accesible en `tusitio.com/admin`
- ✅ **Editor visual** tipo WordPress
- ✅ **Gestión de contenidos**:
  - Noticias (con categorías, imágenes, tags)
  - Blog (con autores, categorías, tiempo de lectura)
  - Campañas (con estadísticas, iconos, botones de acción)
  - Proyectos (con tecnologías, badges, estadísticas)
  - Charlas/Medios (Podcasts, Entrevistas, Charlas)
  - Servicios Corporativos (con características, precios)
- ✅ **Flujo de trabajo editorial** (borradores, revisión, publicación)
- ✅ **Subida de imágenes** arrastrando y soltando
- ✅ **Múltiples usuarios** con diferentes roles

---

## 🛠️ Instalación Paso a Paso

### Paso 1: Crear cuenta en servicios necesarios

1. **GitHub** (gratis): https://github.com/signup
   - Crear una cuenta o usar una existente
   - Esto guardará todo el código y contenido

2. **Netlify** (gratis): https://app.netlify.com/signup
   - Registrarse con la misma cuenta de GitHub
   - Esto publicará el sitio web

### Paso 2: Subir el código a GitHub

1. Crear un nuevo repositorio en GitHub llamado `aca-mov-website`
2. No inicializar con README (ya lo tenemos)
3. Subir todos estos archivos al repositorio:
   ```bash
   # Si usas Git en tu computadora:
   git init
   git add .
   git commit -m "Primer commit"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/aca-mov-website.git
   git push -u origin main
   ```

   **O más fácil**: En GitHub.com, entrar al repo → "Add file" → "Upload files" → subir el ZIP descomprimido

### Paso 3: Conectar con Netlify

1. En Netlify, clic en "Add new site" → "Import an existing project"
2. Elegir GitHub como proveedor
3. Autorizar a Netlify
4. Seleccionar el repositorio `aca-mov-website`
5. Configuración del build:
   - **Build command**: `hugo --gc --minify`
   - **Publish directory**: `public`
   - **Advanced** → Add environment variable:
     - Key: `HUGO_VERSION`
     - Value: `0.124.0`
6. Clic en "Deploy site"

### Paso 4: Configurar autenticación (IMPORTANTE)

1. En Netlify, ir a "Site settings" → "Identity"
2. Clic en "Enable Identity"
3. Ir a "Services" → "Git Gateway" → "Enable Git Gateway"
4. En "Registration", elegir "Invite only" (más seguro) o "Open" (cualquiera puede registrarse)
5. En "External providers", activar Google (opcional pero recomendado)

### Paso 5: Acceder al panel de admin

1. Esperar 2-3 minutos a que termine el deploy
2. Tu sitio estará en: `https://NOMBRE-RANDOM.netlify.app`
3. El panel de admin: `https://NOMBRE-RANDOM.netlify.app/admin`
4. Registrarte con email o Google
5. ¡Listo! Ya puedes empezar a editar contenido

---

## 📝 Cómo usar el panel de administración

### Crear una nueva noticia

1. Ir a `/admin` y hacer login
2. En el menú lateral, clic en "Noticias"
3. Clic en "New Noticias"
4. Completar campos:
   - **Título**: Título de la noticia
   - **Fecha**: Seleccionar fecha de publicación
   - **Categoría**: Elegir de la lista (Legislación, Estadísticas, etc.)
   - **Imagen Destacada**: Subir imagen (arrastrar o clic para buscar)
   - **Extracto**: Resumen corto (aparece en listados)
   - **Tiempo de Lectura**: Ej: "5 min"
   - **Contenido**: Texto completo con editor tipo Word
   - **Destacada**: Activar si va en el slider principal
   - **Tags**: Etiquetas opcionales
5. Clic en "Save" (guarda como borrador) o "Publish" (publica inmediatamente)

### Editar una campaña existente

1. Ir a "Campañas" en el menú lateral
2. Ver lista de campañas
3. Clic en el nombre de la campaña
4. Editar los campos necesarios
5. Guardar cambios

### Subir imágenes

1. En cualquier campo de imagen, clic en "Choose different image"
2. Arrastrar imagen desde tu computadora o clic en "Upload"
3. La imagen se sube automáticamente y se optimiza
4. También puedes usar imágenes ya subidas desde "Media"

### Flujo editorial (borradores)

1. Al crear contenido nuevo, clic en "Save" (no "Publish")
2. El contenido queda en estado "Draft" (borrador)
3. Otros usuarios pueden revisarlo
4. Cuando esté listo, cambiar estado a "Ready" → "Publish"
5. También se puede programar publicación para fecha futura

---

## 🎨 Personalización avanzada

### Cambiar colores del sitio

Editar `assets/css/main.css`:
```css
:root {
  --primary: #1a365d;    /* Azul principal */
  --secondary: #e53e3e;  /* Rojo acento */
  --accent: #38a169;     /* Verde éxito */
}
```

### Modificar estructura de campos

Editar `static/admin/config.yml`:
- Agregar nuevos campos a las colecciones
- Cambiar opciones de selectores
- Agregar nuevas colecciones

### Agregar un nuevo usuario editor

1. En Netlify, ir a "Identity"
2. Clic en "Invite users"
3. Ingresar email del nuevo editor
4. El recibe invitación por correo
5. Al aceptar, puede entrar a `/admin` y editar

---

## 📱 Estructura de archivos

```
aca-mov-website/
├── config.toml              # Configuración de Hugo
├── content/                 # Contenido administrable
│   ├── _index.md           # Página de inicio
│   ├── noticias/           # Noticias (1 archivo por noticia)
│   ├── blog/               # Artículos de blog
│   ├── campanas/           # Campañas
│   ├── proyectos/          # Proyectos
│   ├── charlas/            # Charlas y medios
│   └── servicios/          # Servicios corporativos
├── layouts/                 # Templates HTML
│   ├── _default/           # Templates base
│   └── partials/           # Fragmentos reutilizables
├── static/                  # Archivos estáticos
│   ├── admin/              # Panel de Netlify CMS
│   │   ├── index.html
│   │   └── config.yml      # Configuración del CMS
│   └── images/             # Imágenes subidas
├── assets/                  # CSS y JS procesados
│   ├── css/
│   └── js/
└── README.md               # Este archivo
```

---

## 🔧 Solución de problemas

### No puedo entrar a /admin

- Verificar que Identity esté habilitado en Netlify
- Verificar que Git Gateway esté activado
- Limpiar caché del navegador (Ctrl+F5)

### Los cambios no aparecen en el sitio

- Verificar que se hizo clic en "Publish" (no solo "Save")
- Esperar 1-2 minutos a que Netlify reconstruya el sitio
- Revisar en Netlify → "Deploys" si hay errores

### Error al subir imágenes

- Verificar que `media_folder` en `config.yml` sea correcto
- Las imágenes deben ser JPG, PNG o GIF
- Tamaño máximo recomendado: 5MB

### No se ve el contenido nuevo en el sitio

- Hugo regenera el sitio estático al publicar
- A veces hay que esperar 2-3 minutos
- Forzar redeploy en Netlify: "Deploys" → "Trigger deploy"

---

## 💰 Costos

| Servicio | Costo | Límites |
|----------|-------|---------|
| GitHub | Gratis | Repos ilimitados, públicos o privados |
| Netlify | Gratis | 100GB bandwidth/mes, 300 build minutos/mes |
| Netlify CMS | Gratis | Sin límites |
| Hugo | Gratis | Sin límites |

**Para un sitio de ACA MOV, el plan gratuito es suficiente.**

Si necesitas más:
- Netlify Pro: $19/mes (1TB bandwidth, 1000 build minutos)
- Solo si el sitio tiene +100.000 visitas/mes

---

## 📞 Soporte

Si tienes problemas:

1. **Documentación oficial**:
   - Netlify CMS: https://www.netlifycms.org/docs/
   - Hugo: https://gohugo.io/documentation/

2. **Comunidad**:
   - Foro de Netlify: https://answers.netlify.com/
   - Foro de Hugo: https://discourse.gohugo.io/

3. **Contactar al desarrollador**: [tu-email@ejemplo.com]

---

## 🎉 ¡Listo!

Con esta configuración tienes un sitio web profesional, administrable, seguro y gratuito. El panel de Netlify CMS es muy intuitivo y no requiere conocimientos técnicos para usarlo.

**Tiempo estimado de instalación**: 30-45 minutos
**Nivel de dificultad**: Medio (requiere seguir instrucciones paso a paso)
**Mantenimiento**: Mínimo (solo crear/editar contenido)

---

## 🔄 Actualizaciones futuras

Para actualizar el sitio con nuevas funcionalidades:

1. Descargar nueva versión del código
2. Reemplazar archivos manteniendo la carpeta `/content/` (tu contenido)
3. Subir cambios a GitHub
4. Netlify actualiza automáticamente

**IMPORTANTE**: Siempre hacer backup de la carpeta `content/` antes de actualizar.
