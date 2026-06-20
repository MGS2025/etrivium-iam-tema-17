# Tema 17 — Índice

> **Título oficial**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Diseño de bases de datos: concepto y objetivos**
   1.1. Qué es diseñar una base de datos y por qué importa
   1.2. Los tres niveles de diseño (conceptual, lógico, físico) y el ciclo de vida
   1.3. Objetivos del diseño (integridad, no redundancia, rendimiento, independencia)
   1.4. Diseño conceptual: el modelo entidad-relación (E-R)
   1.5. Diseño lógico
   1.6. Transformación de entidades y relaciones al modelo relacional
   1.7. Eliminación de redundancias
   1.8. Integridad de entidad e integridad referencial
   1.9. Lenguajes de definición y manipulación (DDL, DML, DCL, TCL)
   1.10. Diseño físico
   1.11. Estructuras de datos y de almacenamiento (tablespaces, páginas, particiones)
   1.12. Índices (B-tree, hash, bitmap, agrupado y no agrupado)
   1.13. Rendimiento y optimización (planes de ejecución, particionamiento, clustering)

2. **El modelo lógico relacional**
   2.1. Conceptos básicos (relación, tupla, atributo, dominio, grado, cardinalidad)
   2.2. Claves: candidata, primaria, alternativa, superclave y ajena
   2.3. Reglas de integridad del modelo relacional
   2.4. Álgebra relacional (operadores y consultas)
   2.5. Cálculo relacional (de tuplas y de dominios)
   2.6. Normalización: objetivos, redundancia y anomalías
   2.7. Dependencias funcionales y axiomas de Armstrong
   2.8. Primera Forma Normal (1FN)
   2.9. Segunda Forma Normal (2FN)
   2.10. Tercera Forma Normal (3FN)
   2.11. Forma Normal de Boyce-Codd (BCNF)
   2.12. Formas normales superiores (4FN y 5FN)
   2.13. Desnormalización controlada
   2.14. Buenas prácticas y errores típicos de diseño

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| Diseño de BD | Proceso en 3 niveles: conceptual → lógico → físico |
| Modelo conceptual | Independiente del SGBD; el más usado es el entidad-relación (Chen, 1976) |
| Modelo lógico | Adaptado al tipo de SGBD (relacional); aún independiente del producto |
| Modelo físico | Cómo se almacena realmente: ficheros, índices, particiones (producto concreto) |
| Independencia de datos | Cambiar un nivel sin afectar a los superiores (física y lógica) |
| Relación | Tabla: conjunto de tuplas (filas) sobre un esquema de atributos (columnas) |
| Dominio | Conjunto de valores válidos de un atributo |
| Grado / Cardinalidad | Nº de atributos (columnas) / nº de tuplas (filas) de una relación |
| Clave candidata | Conjunto mínimo de atributos que identifica unívocamente una tupla |
| Clave primaria | Clave candidata elegida; no admite nulos (integridad de entidad) |
| Clave ajena (foránea) | Atributo que referencia la clave primaria de otra tabla (integridad referencial) |
| Integridad de entidad | La clave primaria no puede ser nula ni duplicada |
| Integridad referencial | Toda clave ajena apunta a una fila existente o es nula |
| Álgebra relacional | Lenguaje procedimental: σ (selección), π (proyección), ⋈ (join), ∪, −, ×, ÷ |
| Cálculo relacional | Lenguaje declarativo (qué, no cómo); de tuplas y de dominios |
| Dependencia funcional | X → Y: el valor de X determina el de Y |
| Axiomas de Armstrong | Reflexividad, aumento y transitividad (reglas de inferencia de DF) |
| Anomalías | Problemas de inserción, borrado y actualización por mal diseño |
| 1FN | Atributos atómicos: sin grupos repetitivos ni valores multivaluados |
| 2FN | 1FN + sin dependencias parciales de la clave (atributos dependen de TODA la clave) |
| 3FN | 2FN + sin dependencias transitivas entre atributos no clave |
| BCNF | Todo determinante es clave candidata (3FN reforzada) |
| Desnormalización | Introducir redundancia controlada a propósito para ganar rendimiento |
| Índice | Estructura auxiliar (B-tree, hash, bitmap) que acelera las búsquedas |
| Plan de ejecución | Ruta que elige el optimizador para resolver una consulta |

---

*Tiempo estimado de estudio: 12-14 horas*
*Extensión del contenido: ~12.000-15.000 palabras · 12 diagramas SVG embebidos*
