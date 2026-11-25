# Ciberseguridad — Fases 2 y 3

- [Fase 2: amenazas, vulnerabilidades y riesgos (01/11/2026)](Fase_2_Analisis_de_Riesgos_version_publica.pdf). Define ecosistema, exclusión de ECU 911, revisión de Secrets, Gitleaks, permisos e integridad SHA-256 (pp. 3–6 y anexos).
- [Fase 3: diseño y planificación de controles (22/11/2026)](Fase_3_Controles_de_Seguridad_version_publica.pdf). Prioriza riesgos, tratamiento, seis controles, plan de implementación y validación (pp. 3–8).

**Copias públicas:** se reservan correos personales, firmas y captura de accesos de Drive; también se ocultan líneas de rutas locales en capturas de terminal. Los PDF originales completos se entregan por separado para custodia en Drive restringido. No publicarlos en GitHub sin autorización de las personas involucradas.

| Control | Descripción | Estado reportado en Fase 3 (p. 6) |
|---|---|---|
| CTL-01 | Verificación en dos pasos | Implementado |
| CTL-02 | Alertas y respuesta ante cuenta comprometida | Planificado |
| CTL-03 | Permisos por rol y carpetas separadas | En proceso |
| CTL-04 | Verificación SHA-256 de originales | En proceso |
| CTL-05 | Respaldos semanales (Drive, OneDrive y local) | Implementado |
| CTL-06 | Gitleaks y reglas de publicación | En proceso |

Los estados provienen del informe, no de pruebas nuevas. La Fase 4 deberá validar los controles. No se ha configurado GitHub Actions ni modificado permisos de Drive en esta reorganización. Ver [SECURITY.md](../../SECURITY.md).
