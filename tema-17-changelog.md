# Tema 17 — Changelog

> **Título oficial**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.

---

## v1.1 — 2026-09-06 — Ficha de extensión y tiempo de estudio

**Estado**: sin cambios de contenido. Solo se añade información sobre el propio tema.

**Motivo**: petición del IAM (Jesús Cuadrado, 02-09-2026) al validar el Tema 30. Acepta la extensión de los temas «compuestos» a condición de que se informe de «su extensión en palabras y tiempo estimado de estudio». Al revisarlo se vio que ese dato solo aparecía en 16 de los 40 temas, y que faltaba justo en los más largos.

### Alcance

- Ficha bajo la cabecera del tema, y al final de la pestaña Índice donde esa pestaña existe:
  - **Extensión**: ~10.000 palabras · 12 diagramas · 60 preguntas de test
  - **Tiempo estimado de estudio**: 11-13 horas (primera vuelta completa, sin contar repasos)
- La cifra de palabras de la tabla de entregables se sincroniza con la ficha, para que el tema no muestre dos recuentos distintos.
- Las horas salen de una fórmula común a los 40 temas, para que sean comparables entre sí: contenido a 1.500 palabras/hora (ritmo de estudio activo), diagramas a una hora por cada cinco y test a dos minutos por pregunta. Se publica como intervalo de dos horas.
- Generado con `_tools-qa/ficha_estudio.py`, idempotente y reejecutable tras cualquier regeneración con `build_tNN.py`.

---

## v1.0 — 2026-06-20 — Primera versión

**Estado**: pendiente de validación por María y Ana, y de revisión técnica del IAM (Jesús Cuadrado).

**Motivo**: desarrollo del Tema 17, dentro de la serie de temas técnicos generados desde cero (tras T13, T14 y T15), replicando la estructura y el formato de los Temas 1 y 11 ya validados, e incorporando las mejoras del feedback de Jesús a T13 (pestaña Índice y listas anidadas correctas desde el inicio).

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | ~9.800 palabras · 2 secciones del esqueleto oficial (Diseño de BD; Modelo lógico relacional) con 27 epígrafes |
| Diagramas SVG inline | 12 (accesibles con `role`/`aria-label`) |
| Banco de preguntas tipo test | 60 preguntas A/B/C con explicación y referencia, balanceadas **20/20/20** |
| Casos prácticos | 3 (diseño lógico/expedientes, normalización/licencias, diseño físico/multas) · 10 puntos cada uno |
| Fuentes Tier 1 | 12 referencias canónicas (Codd, Chen, Armstrong, Fagin, Date, Elmasri-Navathe, Silberschatz, Ramakrishnan, ISO 9075/11179) |

### Decisiones de generación

1. **Sin material de cliente**: solo el esqueleto `Test_Prompting/temas junio/17.md`. Desarrollado desde fuentes canónicas de diseño y normalización de bases de datos, todas referenciadas.
2. **Estructura fiel al esqueleto oficial**: dos secciones H2 («Diseño de bases de datos» y «El modelo lógico relacional»), con la normalización anidada en la segunda, tal como aparece en el temario. Se corrigieron 3 erratas del esqueleto de partida (`báaicos`; «Primera Forma Normal» repetida en 2FN y 3FN).
3. **Profundidad ampliada** (decisión de Joan): se buscó un tema extenso. Se añadió, frente a los técnicos previos, material de alto valor de examen: algoritmo del cierre de atributos y cálculo de claves candidatas, recubrimiento mínimo, propiedades de la descomposición (sin pérdida y preservación de dependencias), operadores extendidos del álgebra, internals del B+tree, algoritmos de join y un ejercicio capstone de normalización 1FN→BCNF.
4. **Contexto Ayuntamiento de Madrid** en los casos y ejemplos (Padrón, expedientes, licencias, tributos, multas, callejero, 21 distritos).
5. **Frontera con temas vecinos** cuidada: SGBD y administración al T15; modelo conceptual E-R al T16; SQL/procedimientos al T19; almacenamiento al T26; seguridad al T32/T39.
6. **Referencias cruzadas validadas contra BOAM 10.032**: T13, T15, T16, T19, T26, T32, T39. Todas comprobadas.
7. **Mejoras de T13 v1.1 incorporadas de inicio**: pestaña **Índice** cableada y conversor md→HTML con **listas anidadas** correctas.

### Pendientes para QA / próxima iteración

- Validación de profundidad por María/Ana/IAM (¿alguna sección a ampliar o recortar?).
- Verificación ortográfica con corrector es_ES (cuidado con falsos positivos por términos técnicos en inglés: join, hash, bitmap, cluster, log…).

### Origen

Generado el 2026-06-20 en el flujo de trabajo de eTrivium, replicando el patrón de los Temas 1 (v2.1), 11 (v3.2), 13 (v1.1), 14 (v1.0) y 15 (v1.0). `build_t17.py` y `_build_css.txt` persistidos en el repo.
