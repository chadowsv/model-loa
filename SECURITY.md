# Seguridad y publicación responsable

El repositorio es público según la documentación de Ciberseguridad. Mantener originales, credenciales, evidencias personales, firmas y datos no autorizados fuera de GitHub. Usar Secrets de Colab (`API_Feriados`), acceso restringido a Drive y mínimo privilegio. No introducir tokens en celdas, outputs, URLs, capturas o commits.

## Antes de cada publicación

1. Revisar `git status` y `git diff --cached`; para binarios, abrir los documentos y notebooks.
2. Revisar datos personales, capturas, metadatos, archivos comprimidos y salidas guardadas. No asumir que `.gitignore` elimina archivos ya rastreados.
3. Ejecutar localmente `gitleaks dir --redact .` y, dentro de un clon con historial, `gitleaks git --redact` si la versión instalada admite esos comandos. Revisar resultados antes de hacer push.
4. CTL-06 prevé GitHub Actions, secret scanning y push protection; habilitarlos y verificar disponibilidad en la configuración real del repo. Este ZIP no los configura ni acredita su funcionamiento.
5. Si se expone una clave, revocarla/rotarla de inmediato, revisar actividad y coordinar limpieza del historial. No publicar la clave en un issue.

Los controles y estados se describen en [Ciberseguridad](07_Documentacion/Ciberseguridad/README.md). Notificar incidentes por un canal privado del equipo. No enviar credenciales ni copias de datos personales por canales públicos.
