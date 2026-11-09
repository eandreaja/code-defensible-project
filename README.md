# code-defensible-project

Plantilla del nivel **proyecto**: qué archivos de defensa agregar a un repositorio concreto y cuándo. No se trabaja aquí: se copian a cada proyecto solo las piezas que el proyecto pida. La plantilla hermana para el sistema global es `code-defensible-workflow`.

Este repositorio es solo plantilla: no contiene datos personales.

**Principio:** es un menú, no una lista de tareas. Cada archivo de `plantillas/` se copia al proyecto cuando aparece su disparador.

## 1. Qué tipo de trabajo es

| Tipo | Ejemplos |
|---|---|
| **A. Ejercicio de aprendizaje** | Ejercicios de un curso, pruebas de una librería, práctica de SQL |
| **B. Proyecto propio en crecimiento** | Un agente, un pipeline, una app propia |
| **C. Toca a otros o a datos reales** | Un servicio que usa alguien más, datos de clientes, credenciales reales |
| **D. Script o automatización con acceso** | Una tarea programada o un agente con permisos de ejecución |

**Regla de promoción:** cuando un proyecto B recibe su primer usuario real, pasa a C y se escribe su defensa antes de dejarlo vivo.

## 2. Qué usar según el tipo

`●` desde el inicio · `○` cuando se dé el disparador · `-` no aplica

| Pieza | A | B | C | D |
|---|---|---|---|---|
| `HANDOVER.md` | - | ● | ● | ○ |
| `CONSTRAINTS.md` | - | ● | ● | ● |
| `ALLOW-POLICY.md` | ○ | ● | ● | ● |
| `DECISIONS.md` | - | ○ | ● | ● |
| `FLOW.md` | - | ○ | ● | ○ |
| `ROLLBACK.md` | - | ○ | ● | ● |
| `THREAT.md` / `FAILURE.md` | - | ○ | ● | ● |
| `DEFENSE.md` | - | - | ● | ○ |
| `ALTERNATIVES.md` | - | - | ○ | - |
| `MAPA-DE-APRENDIZAJE.md` | ● | ● | ○ | - |
| Teach-back | ● | ● | ● | ○ |

Mínimo viable: **A** explicar lo que hizo la IA y anotar lo que no se supo; **B** `HANDOVER` + `CONSTRAINTS` + `ALLOW-POLICY`; **C** B + `DECISIONS` + `THREAT` + `FAILURE` + `ROLLBACK`, y `DEFENSE` antes de entregar; **D** `CONSTRAINTS` + `DECISIONS` + `ROLLBACK` + una `ALLOW-POLICY` estricta.

## 3. Disparadores

| Si pasa esto | Agrega |
|---|---|
| Tienes que volver a explicar el contexto al empezar una sesión | `HANDOVER.md` |
| Te preguntas por qué elegiste una librería o un patrón | `DECISIONS.md` |
| Un error vive entre archivos y no sabes por dónde entra la ejecución | `FLOW.md` |
| La IA tocó algo que no debía | `CONSTRAINTS.md` |
| Vas a hacer un cambio grande o riesgoso | `ROLLBACK.md` (anota el último commit bueno) |
| Alguien más va a usar lo que hiciste | `THREAT.md`, `FAILURE.md` y luego `DEFENSE.md` |
| Descartaste opciones y no recuerdas por qué | `ALTERNATIVES.md` |
| No puedes explicar algo que la IA hizo | `MAPA-DE-APRENDIZAJE.md` |
| Te cansas de decidir en cada ventana de permiso | `ALLOW-POLICY.md` |

## 4. Especificación: Spec Kit, no SPEC.md

En los proyectos se usa **Spec Kit** (`.specify/`), que se ejecuta dentro de cada proyecto. Por eso aquí **no** se crea `SPEC.md`: dos formatos de especificación para lo mismo solo confunden. Spec Kit se aplica cuando hay algo que construir; para estudiar un tema bastan `MAPA-DE-APRENDIZAJE.md` y el teach-back.

## 5. Teach-back

Al terminar, elige una cosa que hizo la IA y explícala sin mirar el chat. Si no puedes, es una tarea de estudio, no un fracaso. Pide a la IA que actúe como revisora escéptica y responde de memoria:

1. ¿Por qué hiciste X y no Y?
2. ¿Qué pasa si un actor se comporta de forma maliciosa?
3. ¿Qué estructura de datos usaste y por qué?
4. ¿Dónde falla esto?

## 6. Banderas rojas en un diff

| Lo que ves | Pregúntate |
|---|---|
| Pruebas borradas o saltadas | ¿Por qué se achica la red de seguridad? |
| Validación o autenticación aflojada | ¿Quién se beneficia? |
| Paquete o llamada de red nueva | ¿Sé qué es y quién lo ejecuta? |
| Valores, claves o URLs escritos a mano | ¿Dónde debería vivir esto? |
| Diff enorme para un pedido pequeño | ¿Qué más cambió que no pedí? |
| Una regla `allow` nueva con una credencial escrita en el comando | ¿Por qué hay un secreto en una regla? |

## 7. Reglas de permisos en Claude Code

Los tres cubos de `ALLOW-POLICY.md` se aplican así: Seguro con `allow`, Nunca con `deny`. Para Pausar, la ausencia de `allow` pide permiso, salvo que el modo de permisos decida solo; las reglas `ask` explícitas **no están probadas** aquí.

- En el `settings.json` **de usuario**, las rutas de `deny` van ancladas: `Read(//**/.env)` o `Read(~/...)`.
- `Read(./.env)` solo vale dentro de un proyecto.
- Confirma con `/status` qué archivos de configuración se cargaron y revisa la sintaxis en la documentación de tu versión.

## 8. Archivos incluidos

`AGENTS.md` (mapa inicial para el agente) y `plantillas/` (las plantillas de cada archivo).

## Origen y licencia

Adaptado de "Stop Clicking Allow" (Rohan Mistry, Medium, nov 2026). La matriz, los disparadores y `MAPA-DE-APRENDIZAJE.md` son criterio propio, sin medir. Licencia pendiente de decidir; sin archivo `LICENSE`, todos los derechos están reservados.
