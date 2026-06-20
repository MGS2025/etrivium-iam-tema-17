# Tema 17 — Checklist de Validación

> **Título oficial**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-06-20
> **Revisores**: María y Ana (eTrivium) · revisión técnica IAM (Jesús Cuadrado)
> **Instrucciones**: marcar cada ítem. Los cambios no se guardan en la web (imprimir o exportar a PDF si se desea fijarlos).

---

## 1. Cobertura del temario oficial

- [ ] **Diseño de bases de datos**: concepto, objetivos, niveles conceptual/lógico/físico, ciclo de vida — §1.1-1.3
- [ ] **Diseño lógico**: transformación E-R → relacional, eliminación de redundancias, integridad, DDL/DML/DCL/TCL — §1.5-1.9
- [ ] **Diseño físico**: estructuras de almacenamiento, índices, rendimiento, planes de ejecución, particionamiento — §1.10-1.13
- [ ] **Modelo lógico relacional**: conceptos, claves, integridad, álgebra y cálculo relacional — §2.1-2.5
- [ ] **Normalización**: anomalías, dependencias funcionales, 1FN-2FN-3FN-BCNF, 4FN/5FN, desnormalización — §2.6-2.13

## 2. Contenido teórico

- [ ] El nivel de profundidad es adecuado para C1 (¿hay que ampliar alguna sección?)
- [ ] Las definiciones de las formas normales (1FN-BCNF) y de las dependencias funcionales son correctas
- [ ] El álgebra relacional (operadores primitivos vs derivados) y su equivalencia con el cálculo son correctos
- [ ] La frontera con el Tema 15 (SGBD/administración), el Tema 16 (modelo conceptual) y el Tema 19 (SQL) está clara
- [ ] Los ejemplos Ayto Madrid (Padrón, expedientes, licencias, tributos, multas) son verosímiles

## 3. Fuentes

- [ ] Todas las afirmaciones técnicas están respaldadas por fuente Tier 1
- [ ] Las referencias inline se corresponden con `tema-17-fuentes.md`
- [ ] Atribuciones históricas correctas (Codd 1970/1972, Boyce-Codd 1974, Chen 1976, Armstrong 1974, Fagin 1977)

## 4. Test (60 preguntas)

- [ ] Cada pregunta tiene una sola respuesta correcta e inequívoca
- [ ] Los distractores (A/B/C) son plausibles
- [ ] La distribución de la opción correcta entre A/B/C está equilibrada (20/20/20 tras QA)
- [ ] Las explicaciones y referencias de cada respuesta son correctas

## 5. Casos prácticos (3)

- [ ] Realistas y propios del Ayuntamiento (expedientes, licencias, multas/cuadro de mando)
- [ ] Soluciones orientativas técnicamente correctas
- [ ] La puntuación de cada caso suma 10 puntos

## 6. Diagramas (12 SVG)

- [ ] Cada diagrama es correcto y legible (también impreso en B/N)
- [ ] Accesibilidad: todos tienen `role="img"` y `aria-label`

## 7. Referencias cruzadas a otros temas

- [ ] Validadas contra BOAM 10.032 (T13, T15, T16, T19, T26, T32, T39)
- [ ] Ninguna referencia cruzada cita un enunciado de tema incorrecto

## 8. Calidad editorial

- [ ] Ortografía verificada (tildes y ñ) — sin diacríticos perdidos
- [ ] Coherencia de versión (v1.0) en title, badges, banner y footer del `index.html`
- [ ] El `index.html` abre, navega entre las 8 pestañas y el motor de test funciona
- [ ] Las listas anidadas del Contenido se muestran con sus niveles (sin aplanar)

---

## Observaciones abiertas

_(Espacio para anotaciones de María, Ana y la revisión IAM.)_
