# Cabalgatas en Viñales

Sitio estático bilingüe (español/inglés), responsive y sin dependencias de build. Puedes abrir `index.html` o usar Live Server en Visual Studio Code.

## Antes de publicar

1. Edita `BUSINESS` al inicio de `script.js`: número de WhatsApp en formato internacional sin `+` y URL exacta del perfil del negocio en Tripadvisor. Cambia también los enlaces a Instagram, Facebook y Google Maps en `index.html`.
2. Coloca tus fotos propias en `assets/img/` con estos nombres: `vinales-hero.webp` (fondo, 1920 × 1080 o mayor, idealmente menos de 500 KB), `vinales-hero-mobile.webp` (fondo móvil, versión vertical/comprimida), `vinales-hero.jpg` (fallback del fondo) y `vinales-galeria-1.webp`, `vinales-galeria-2.webp`, `vinales-galeria-3.webp` (galería). `index.html` ya apunta a esas rutas; si cambias los nombres, actualiza los atributos `src`, `srcset`, `data-lightbox` y `og:image`. Ajusta el texto alternativo (`alt` y `data-alt`) para describir tus fotos.
3. Personaliza nombre legal, datos de contacto, precios reales, condiciones del recorrido, texto de privacidad, mapa y redes. Los precios se consultan por mensaje para no publicar tarifas inventadas.
4. El perfil de Tripadvisor configurado es `Vinales On Horseback` (ID `d24100695`). La mención a N.º 1 en actividades al aire libre en Viñales y Travellers' Choice 2026 se incorporó según los datos proporcionados por el negocio; confirma que coincidan exactamente con el reconocimiento visible en tu perfil y conserva evidencia actualizada.
5. No copies reseñas ni descargues/republiques fotos de Tripadvisor sin autorización. La galería de esta plantilla conserva imágenes temporales propias y enlaza a las fotos/reseñas originales en el perfil. Puedes solicitar a Tripadvisor un widget oficial y seguir sus condiciones; revisa CSP antes de integrarlo.
6. Sustituye `https://cabalgatas-vinales.example` en `sitemap.xml` y `robots.txt` por el dominio definitivo. Configura ese dominio en la plataforma antes de enviar el sitemap a Search Console.
7. El bloque de anfitrión, itinerario y datos de reserva se basa en la ficha pública de Airbnb [`Viñales a caballo`](https://es.airbnb.com/experiences/6856658): Yosbel, duración aproximada de 4 h 30 min, punto de encuentro, instrucción inicial, cabalgata por el valle, finca de tabaco, mirador, idiomas y precio publicado desde $20 USD. El texto del sitio sobre todas las edades y tamaño de grupo flexible refleja la información confirmada directamente por el negocio; la ficha de Airbnb consultada aún indicaba 18+ y un máximo de 10. Actualiza allí esas condiciones si también aplican a las reservas de Airbnb para evitar discrepancias.

## Ejecutar localmente

- Abrir `index.html` directamente funciona para la mayoría de las interacciones.
- Para probar como sitio, abre la carpeta con VS Code y selecciona **Open with Live Server**. El formulario abre WhatsApp con un mensaje prellenado; el visitante lo revisa y lo envía desde WhatsApp.
- No pruebes CSP/cabeceras al abrir `file://`; Live Server tampoco simula las cabeceras del hosting. Compruébalas en un despliegue de prueba con las herramientas del navegador.

## Despliegue estático

- **Netlify:** importa la carpeta/repository, deja el directorio de publicación en la raíz (`.`) y despliega. `_headers` define las cabeceras. Activa **Enforce HTTPS** en Domain management y verifica el dominio antes de habilitar HSTS.
- **Cloudflare Pages:** conecta el repositorio y publica la raíz; no se necesita comando de build. `_headers` configura las cabeceras. En el panel SSL/TLS activa **Always Use HTTPS** y usa una configuración TLS estricta.
- **Vercel:** importa el proyecto como sitio estático sin framework ni build command. `vercel.json` aplica las cabeceras y Vercel sirve el sitio por HTTPS. Asocia el dominio y comprueba la redirección HTTP antes de publicar.
- Revisa que `https://tu-dominio/404.html` aparezca para rutas inexistentes, que los enlaces no apunten a datos de ejemplo y que el `Content-Security-Policy` no reporte errores.
- HSTS es persistente en navegadores. No publiques `Strict-Transport-Security` hasta que HTTPS esté funcionando en todo el dominio; el valor incluido no activa `includeSubDomains` ni `preload`.

## Formulario: alcance y puesta en producción

La página valida nombre, fecha, mensaje y consentimiento en el cliente, limita longitudes y contiene un campo honeypot. Al continuar abre WhatsApp con un texto prellenado y la persona decide si lo envía; este sitio **no envía ni almacena solicitudes en un servidor**. El tratamiento posterior de esos mensajes depende de WhatsApp. Estas comprobaciones no sustituyen validación, rate limiting, CSRF ni protección contra bots en backend. El honeypot del cliente no es una defensa efectiva frente a bots dirigidos y un sitio estático no puede emitir un token CSRF secreto.

Para recibir solicitudes en producción, conecta un servicio de formularios o un backend HTTPS y:

- Configura endpoint y dominio permitidos en el proveedor; no pongas claves privadas en JavaScript.
- Revalida y normaliza todos los campos en servidor, limita tamaño/rate, codifica la salida y usa consultas parametrizadas si hay base de datos.
- Añade protección CSRF acorde a la arquitectura (token ligado a sesión/cookie `SameSite` en backend propio) y controles anti-spam del proveedor o CAPTCHA con verificación servidor-servidor.
- Informa al usuario del tratamiento de sus datos, limita retención y registra errores sin guardar el texto personal de los mensajes.
- Actualiza CSP solo con los dominios de envío/verificación que realmente necesites y vuelve a probarla.

## Tripadvisor: opciones de integración

1. **Widget oficial:** desde las herramientas de Tripadvisor copia el widget autorizado para el perfil `d24100695`. Inserta únicamente el código oficial vigente. Revisa sus términos, el consentimiento/privacidad aplicable y agrega a CSP los orígenes que el widget documente; esta CSP por defecto bloquea scripts externos. No copies ni alteres reseñas protegidas.
2. **Reseñas manuales:** publica solo fragmentos reales verificables, con atribución, fecha y enlace al perfil oficial y autorización para reproducirlos; actualízalos y retíralos si dejan de estar disponibles. En esta plantilla se enlaza a la página oficial para ver las reseñas y fotos originales.
3. **Content API oficial:** requiere acceso/aprobación y puede tener límites y condiciones. Consume la API desde un backend propio, mantén las credenciales fuera del navegador, respeta atribución, caché y términos vigentes. No existe integración API activa en este proyecto.

## Seguridad aplicada y límites

- [x] Sin dependencias JavaScript ni claves API en frontend; scripts locales con `defer`.
- [x] Navegación por teclado, etiquetas de formulario, errores accesibles, enlace para saltar contenido y preferencia `prefers-reduced-motion`.
- [x] Datos del formulario codificados como mensaje prellenado en WhatsApp; el visitante decide enviarlo. Validación cliente y campos con longitudes limitadas.
- [x] Enlaces externos de salida con `target="_blank"` incluyen `rel="noopener noreferrer"`.
- [x] CSP restrictiva y cabeceras X-Content-Type-Options, X-Frame-Options, Referrer-Policy, Permissions-Policy y HSTS en configuraciones de hosting.
- [x] No hay cookies de analítica/publicidad; preferencias de tema/idioma/aviso se guardan en localStorage.
- [ ] Imágenes, nombre y URLs de ejemplo pendientes de datos autorizados del negocio.
- [ ] HTTPS, cabeceras, formulario servidor, CSRF real, anti-spam servidor, consentimiento/legalidad local y pruebas Lighthouse deben verificarse/configurarse en el hosting antes del uso comercial.

La configuración de seguridad debe revisarse con el widget, proveedor de fuentes y endpoint que finalmente se integren. Las obligaciones de privacidad dependen de la entidad y jurisdicciones aplicables; solicita revisión legal local.
