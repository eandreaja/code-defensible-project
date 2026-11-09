# AGENTS

Mapa para el agente. Mantenelo corto: enlaza, no duplica.

## Archivos de trabajo

- `HANDOVER.md`: estado vivo del trabajo (hecho, en curso, roto, siguiente y qué no tocar).
- `docs/CONSTRAINTS.md`: reglas y límites obligatorios.
- `docs/ALLOW-POLICY.md`: qué se aprueba, qué se pausa y qué nunca se permite.
- `docs/DECISIONS.md`: decisiones tomadas y su justificación.
- `docs/ROLLBACK.md`: cómo revertir un cambio riesgoso.
- `docs/THREAT.md` y `docs/FAILURE.md`: amenazas y modos de falla.
- `docs/DEFENSE.md`: resumen de una página para la pizarra.
- `.specify/`: especificación del proyecto con Spec Kit (no hay `SPEC.md`).

Los archivos de esta lista se crean cuando aparece su disparador. Si un archivo todavía no existe, no lo inventes.

## Regla general

Al iniciar una sesión, leé `HANDOVER.md`. Antes de cambiar reglas, permisos o decisiones, consultá el archivo que corresponda en `docs/`. Si hay que romper una regla de `CONSTRAINTS.md`, pará y preguntá.
