# ALLOW-POLICY — qué apruebo, qué pauso y qué nunca permito
> Se decide una vez, con calma y descansada, no en cada popup. Última revisión: AAAA-MM-DD · Herramienta: Claude Code / n8n / otra

| Cubo | Qué entra | Cómo se aplica |
|---|---|---|
| **Seguro** (sin preguntar) | Leer y buscar en mis carpetas de trabajo; comandos de solo lectura; pruebas y linters | Reglas `allow` sin comodín peligroso |
| **Pausar y leer** | Ejecutar código, instalar paquetes, red (`curl`, `gh`), borrar, editar muchos archivos, cambiar configuración | Reglas `ask` explícitas. Elijo "Sí" puntual, nunca "Sí, y no volver a preguntar" |
| **Nunca** (se bloquea) | Leer o escribir `.env`, llaves (`*.pem`, `*.key`, `id_rsa*`), `~/.ssh`, credenciales; contraseñas escritas dentro de un comando | Reglas `deny` en `settings.json` |

## Reglas que me sirven
- **Con `defaultMode: auto`, la ausencia de `allow` no pausa nada:** el comando corre sin preguntar. Para pausar de verdad hacen falta reglas `ask`. Probalo con un comando inofensivo.
- Una regla `ask` mira el comando tal como se escribe: no atrapa el mismo comando lanzado a través de otro programa.
- Las rutas de `deny` en el `settings.json` de **usuario** van ancladas: `Read(//**/.env)` o `Read(~/...)`. `Read(./.env)` solo vale dentro de un proyecto.
- Un `allow` nuevo entra solo si puedo explicar por qué es seguro (la prueba de la pizarra).
- Una regla que apruebo "para siempre" sin pensar es un `allow` ciego: revisala en la próxima auditoría.

## Revisión
- Cuándo: en cada auditoría periódica. Cómo: contá las reglas `allow`/`deny`/`ask` (sin imprimir su contenido) y buscá secretos en los `settings*.json`.
- Respaldo antes de cada cambio: carpeta + hash.

## Pendientes / decisiones abiertas
- [ ] ¿Qué comandos van en `ask`? Empezá angosto (instalar, red, borrar, push forzado) y ampliá con la experiencia.
- [ ] ¿Deben coincidir el `defaultMode` de todos mis entornos?
