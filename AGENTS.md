# AGENTS

Mapa para el agente. Mantenerlo corto: enlaza, no duplica.

## Archivos de trabajo

- `HANDOVER.md`: estado vivo del trabajo (hecho, en curso, roto, siguiente y qué no tocar).
- `docs/CONSTRAINTS.md`: reglas y límites obligatorios.
- `docs/ALLOW-POLICY.md`: qué se aprueba, qué se pausa y qué nunca se permite.
- `docs/DECISIONS.md`: decisiones tomadas y su justificación.
- `docs/ROLLBACK.md`: cómo revertir un cambio riesgoso.
- `docs/THREAT.md` y `docs/FAILURE.md`: amenazas y modos de falla.
- `docs/DEFENSE.md`: resumen de una página para la pizarra.
- `.specify/`: especificación del proyecto con Spec Kit (no hay `SPEC.md`).

Los archivos de esta lista se crean cuando aparece su disparador. Si un archivo no existe todavía, no lo inventes.

## Regla general

Al iniciar una sesión, lee `HANDOVER.md`. Antes de cambiar reglas, permisos o decisiones, consulta el archivo correspondiente en `docs/`. Si una regla de `CONSTRAINTS.md` hay que romperla, para y pregunta.
