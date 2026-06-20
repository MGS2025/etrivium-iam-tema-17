# Tema 17 — Fuentes

> **Título oficial**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.
>
> **Criterio**: todo dato del contenido cita un **ID** inline (p. ej. `[CODD70, §3]`). Tier 1 = fuentes canónicas y normas; Tier 2 = manuales y documentación de producto; Tier 3 = material de apoyo no citado directamente.

---

## Tier 1 — Canónicas y normativas

| ID | Referencia |
|---|---|
| `[CODD70]` | Codd, E. F. (1970). *A Relational Model of Data for Large Shared Data Banks*. Communications of the ACM, 13(6). Artículo fundacional del modelo relacional. |
| `[CODD72]` | Codd, E. F. (1972). *Further Normalization of the Data Base Relational Model*. IBM Research. Define 2FN y 3FN. |
| `[CODD74BCNF]` | Codd, E. F.; Boyce, R. F. (1974). Forma Normal de Boyce-Codd (BCNF). |
| `[CHEN76]` | Chen, P. P. (1976). *The Entity-Relationship Model — Toward a Unified View of Data*. ACM TODS, 1(1). Modelo entidad-relación. |
| `[ARMSTRONG74]` | Armstrong, W. W. (1974). *Dependency Structures of Data Base Relationships*. Axiomas de inferencia de dependencias funcionales. |
| `[FAGIN77]` | Fagin, R. (1977). *Multivalued Dependencies and a New Normal Form (4FN)*. ACM TODS. |
| `[DATE]` | Date, C. J. *An Introduction to Database Systems* (8.ª ed.). Addison-Wesley. Referencia general de modelo relacional, álgebra, cálculo y normalización. |
| `[ELMASRI]` | Elmasri, R.; Navathe, S. B. *Fundamentals of Database Systems* (7.ª ed.). Pearson. Diseño conceptual/lógico/físico y E-R. |
| `[SILBER]` | Silberschatz, A.; Korth, H.; Sudarshan, S. *Database System Concepts* (7.ª ed.). McGraw-Hill. |
| `[RAMAKRISHNAN]` | Ramakrishnan, R.; Gehrke, J. *Database Management Systems* (3.ª ed.). McGraw-Hill. Diseño físico, índices y optimización. |
| `[ISO9075]` | ISO/IEC 9075:2023 *Information technology — Database languages — SQL*. Norma del lenguaje SQL (DDL/DML/DCL/TCL). |
| `[ISO11179]` | ISO/IEC 11179 *Metadata Registries*. Gobierno de metadatos y diccionario de datos. |

## Tier 2 — Manuales y documentación de producto

| ID | Referencia |
|---|---|
| `[PG-DOC]` | PostgreSQL Global Development Group. *PostgreSQL Documentation* — Indexes, EXPLAIN, Partitioning. postgresql.org/docs |
| `[ORA-CONCEPTS]` | Oracle. *Database Concepts* — Schema Objects, Indexes, Tablespaces, Optimizer. |
| `[MS-SQL-INDEX]` | Microsoft. *SQL Server — Clustered and Nonclustered Indexes, Execution Plans*. learn.microsoft.com |
| `[MYSQL-DOC]` | Oracle. *MySQL Reference Manual* — InnoDB, Optimization, Partitioning. |

## Tier 3 — Marco normativo del puesto (contexto, no contenido técnico)

| ID | Referencia |
|---|---|
| `[RGPD]` | Reglamento (UE) 2016/679 (RGPD) — minimización y exactitud de datos en el diseño. |
| `[LOPDGDD]` | Ley Orgánica 3/2018 de Protección de Datos y Garantía de los Derechos Digitales. |
| `[ENS]` | Real Decreto 311/2022, Esquema Nacional de Seguridad — integridad y trazabilidad. |
| `[BOAM10032]` | BOAM 10.032 (23-dic-2025). Bases específicas TIC C1 Ayto. Madrid — temario oficial. |

---

*Las referencias Tier 1 son la base del contenido; Tier 2 ilustra la materialización en productos reales; Tier 3 enmarca el cumplimiento aplicable al Ayuntamiento de Madrid.*
