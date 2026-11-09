# ALLOW-POLICY — qué apruebo, qué pauso y qué nunca permito
> Se decide una vez, con calma y descansada, no en cada popup. Última revisión: AAAA-MM-DD · Herramienta: Claude Code / n8n / otra

| Cubo | Qué entra | Cómo se aplica |
|---|---|---|
| **Seguro** (sin preguntar) | Leer y buscar en mis carpetas de trabajo; comandos de solo lectura; pruebas y linters | Reglas `allow` sin comodín peligroso |
| **Pausar y leer** | Ejecutar código, instalar paquetes, red (`curl`, `gh`), borrar, editar muchos archivos, cambiar configuración | Sin regla `allow` (pide permiso) o regla `ask`. Elijo "Sí" puntual, nunca "Sí, y no volver a preguntar" |
| **Nunca** (se bloquea) | Leer o escribir `.env`, llaves (`*.pem`, `*.key`, `id_rsa*`), `~/.ssh`, credenciales; contraseñas escritas dentro de un comando | Reglas `deny` en `settings.json` |

## Reglas que me sirven
- Rutas de `deny` en el `settings.json` de **usuario** van ancladas (`Read(//**/.env)` o `Read(~/...)`); `Read(./.env)` solo vale dentro de un proyecto.
- Un `allow` nuevo entra solo si puedo explicar por qué es seguro (la prueba de la pizarra).
- Una regla que apruebo "para siempre" sin pensar es un `allow` ciego: revisar en la próxima auditoría.

## Revisión
- Cuándo: en cada auditoría periódica. Cómo: contar reglas `allow`/`deny`/`ask` (sin imprimir su contenido) y buscar secretos en los `settings*.json`.
- Respaldo antes de cada cambio: carpeta + hash.

## Pendientes / decisiones abiertas
- [ ] ¿Uso reglas `ask` explícitas para el cubo "pausar"?
- [ ] ¿Deben coincidir el `defaultMode` de todos mis entornos?
