# Tema 17 — Casos Prácticos

> **Título oficial**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos recorren las tres partes del tema: el **Caso 1** trabaja el **diseño lógico** (transformación del modelo E-R a tablas e integridad) sobre los expedientes; el **Caso 2**, la **normalización** (anomalías y paso a 3FN) sobre las licencias; y el **Caso 3**, el **diseño físico y las consultas** (índices, plan de ejecución, desnormalización) sobre las multas y el cuadro de mando.

---

## Caso 1 — Diseño lógico del registro de expedientes

### Enunciado

El Ayuntamiento gestiona **expedientes administrativos**. De cada expediente se conoce su número, la fecha de apertura y el procedimiento al que pertenece. Un **procedimiento** (licencia de obra, multa, ayuda social…) tiene un código y una denominación. En cada expediente intervienen uno o varios **interesados** (ciudadanos), identificados por su DNI y nombre, y un mismo ciudadano puede figurar en muchos expedientes. Además, cada expediente está asignado a **una** unidad tramitadora, y una unidad tramita muchos expedientes. Debe diseñar el esquema relacional.

### Cuestiones

**Cuestión 1 — Entidades y claves (2 puntos).** Identifique las entidades del problema y proponga la clave primaria de cada una.

**Cuestión 2 — Relación 1:N (2 puntos).** ¿Cómo se representa la relación «una unidad tramita muchos expedientes» en el modelo relacional? Indique dónde va la clave ajena.

**Cuestión 3 — Relación N:M (3 puntos).** La relación entre EXPEDIENTE e INTERESADO es N:M. Diseñe la solución relacional completa, con la tabla resultante, su clave primaria y sus claves ajenas.

**Cuestión 4 — Integridad (3 puntos).** Explique qué reglas de integridad (de entidad y referencial) garantizan que: (a) no exista un expediente sin número; (b) no se asigne un expediente a una unidad inexistente. Proponga la política referencial al intentar borrar una unidad que aún tramita expedientes.

### Solución orientativa

- **C1**: Entidades `PROCEDIMIENTO(cod_proc PK)`, `EXPEDIENTE(num_exp PK)`, `INTERESADO(dni PK)`, `UNIDAD(cod_unidad PK)`. Las claves naturales son cod_proc, num_exp, dni y cod_unidad. *(§1.4, §2.2)*
- **C2**: Es una relación **1:N** → la clave de UNIDAD se **propaga** como clave ajena en EXPEDIENTE: `EXPEDIENTE(num_exp PK, fecha_apertura, cod_proc FK, cod_unidad FK)`. No se crea tabla nueva. *(§1.6)*
- **C3**: La N:M se resuelve con una **tabla intermedia**: `INTERVENCION(num_exp, dni, rol, PK(num_exp, dni))` con dos claves ajenas (`num_exp → EXPEDIENTE`, `dni → INTERESADO`). El atributo `rol` (titular, representante…) es propio de la relación. *(§1.6)*
- **C4**: (a) la **integridad de entidad** impide que `num_exp` (clave primaria) sea nulo; (b) la **integridad referencial** sobre `cod_unidad` impide asignar el expediente a una unidad inexistente. Al borrar una unidad con expedientes, la política adecuada es `RESTRICT/NO ACTION` (rechazar el borrado) para no dejar expedientes huérfanos. *(§1.8)*

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Identifica entidades y claves primarias correctas | 2 |
| Resuelve la 1:N propagando la clave ajena al lado «N» | 2 |
| Diseña la tabla intermedia N:M con clave compuesta y dos FK | 3 |
| Explica integridad de entidad y referencial + política RESTRICT | 3 |

---

## Caso 2 — Normalización del registro de licencias

### Enunciado

Un sistema antiguo guarda las licencias de actividad en **una sola tabla**:

`LICENCIA(num_lic, titular_dni, titular_nombre, cod_distrito, nombre_distrito, tasa_distrito, tecnicos)`

donde `tecnicos` contiene los nombres de los técnicos asignados separados por comas, `nombre_distrito` y `tasa_distrito` dependen del `cod_distrito`, y `titular_nombre` depende del `titular_dni`. Se han detectado incoherencias: el mismo distrito aparece con nombres distintos y, al borrar la última licencia de un distrito, se pierde su tasa.

### Cuestiones

**Cuestión 1 — Anomalías (2 puntos).** Identifique y nombre las tres anomalías presentes, con un ejemplo de cada una sobre estos datos.

**Cuestión 2 — 1FN (2 puntos).** ¿Qué regla viola el atributo `tecnicos`? Normalice la tabla a 1FN.

**Cuestión 3 — 2FN y 3FN (4 puntos).** Lleve el diseño hasta la 3FN explicando, en cada paso, qué tipo de dependencia se elimina (parcial o transitiva) y mostrando las tablas resultantes con sus claves.

**Cuestión 4 — Justificación (2 puntos).** ¿Por qué el diseño normalizado elimina las incoherencias detectadas? ¿Hasta qué forma normal es razonable llegar aquí y por qué?

### Solución orientativa

- **C1**: **Inserción** (no se puede registrar un distrito nuevo sin una licencia); **borrado** (borrar la última licencia de un distrito elimina su nombre y tasa); **actualización** (cambiar el nombre del distrito obliga a tocar todas las filas, y olvidar alguna genera la incoherencia observada). *(§2.6)*
- **C2**: `tecnicos` viola la **1FN** (varios valores en una celda, no atómico). Se extrae: `LICENCIA(num_lic PK, titular_dni, titular_nombre, cod_distrito, nombre_distrito, tasa_distrito)` y `ASIGNACION(num_lic, tecnico, PK(num_lic, tecnico))`. *(§2.8)*
- **C3**: La clave de LICENCIA es simple (`num_lic`) → no hay dependencias **parciales**, ya está en **2FN**. Pero hay dependencias **transitivas**: `num_lic → cod_distrito → {nombre_distrito, tasa_distrito}` y `num_lic → titular_dni → titular_nombre`. Para la **3FN** se separan: `DISTRITO(cod_distrito PK, nombre_distrito, tasa_distrito)`, `TITULAR(titular_dni PK, titular_nombre)` y `LICENCIA(num_lic PK, titular_dni FK, cod_distrito FK)`. *(§2.9, §2.10)*
- **C4**: Cada hecho (nombre y tasa del distrito, nombre del titular) se almacena **una sola vez**, así que no puede quedar inconsistente, se puede dar de alta un distrito sin licencias y borrar una licencia no afecta al distrito. Llegar a **3FN** es suficiente: aquí cada determinante de las tablas resultantes es clave, por lo que también cumplen BCNF, sin necesidad de formas superiores. *(§2.6, §2.10, §2.11)*

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Nombra las tres anomalías con ejemplos correctos | 2 |
| Detecta la violación de 1FN y la corrige con tabla aparte | 2 |
| Alcanza la 3FN distinguiendo dependencia parcial vs transitiva | 4 |
| Justifica la eliminación de incoherencias y el grado de normalización | 2 |

---

## Caso 3 — Diseño físico y consultas sobre las multas de tráfico

### Enunciado

La base de datos de **multas de tráfico** tiene una tabla `MULTA(id, matricula, dni_conductor, cod_distrito, fecha_denuncia, importe, estado)` con más de 20 millones de filas. Las consultas más frecuentes son: (a) buscar multas por **matrícula**; (b) listar multas de un **rango de fechas**; (c) un **informe analítico anual** con el total recaudado por distrito. El equipo se queja de lentitud y de que la carga nocturna de nuevas denuncias tarda demasiado.

### Cuestiones

**Cuestión 1 — Índices (3 puntos).** Proponga índices para las consultas (a) y (b), indicando el tipo de índice y por qué. ¿Qué efecto tienen los índices sobre la carga nocturna?

**Cuestión 2 — Plan de ejecución (2 puntos).** La consulta por matrícula hace un *full table scan*. ¿Qué herramienta usaría para comprobarlo y qué dato necesita el optimizador para elegir bien el plan?

**Cuestión 3 — Particionamiento (2 puntos).** ¿Cómo organizaría físicamente la tabla para que el informe anual no recorra los 20 millones de filas? Nombre la técnica y el beneficio.

**Cuestión 4 — Desnormalización (3 puntos).** Para el cuadro de mando, ¿qué técnica aplicaría y qué contrapartida asume? Distinga el tratamiento entre el sistema transaccional (altas diarias) y el analítico.

### Solución orientativa

- **C1**: Para (a), índice **B-tree** sobre `matricula` (igualdad, columna selectiva). Para (b), índice **B-tree** sobre `fecha_denuncia` (soporta rangos). Los índices **aceleran las lecturas** pero **penalizan la carga nocturna**, porque cada INSERT debe actualizar todos los índices: hay que equilibrar. *(§1.12)*
- **C2**: `EXPLAIN` (PostgreSQL/MySQL) o `EXPLAIN PLAN` (Oracle) muestra el plan. El optimizador necesita **estadísticas actualizadas** (cardinalidad, distribución de valores) para estimar costes; conviene ejecutar `ANALYZE`. Si tras crear el índice sigue el *full scan*, suele ser por estadísticas desactualizadas o por una función sobre la columna. *(§1.13)*
- **C3**: **Particionar** la tabla **por rango de fecha (por año)**. El informe del ejercicio en curso lee solo la partición correspondiente (*partition pruning*) en vez de los 20 millones de filas; además facilita el mantenimiento y el archivado. *(§1.13)*
- **C4**: Una **vista materializada** (o tabla de resumen) con el total recaudado por distrito y año, que evita recalcular el agregado en cada acceso. Contrapartida: hay que **refrescarla** y asume **redundancia controlada**. El sistema **transaccional** se mantiene **normalizado** (integridad de las altas); el **analítico/cuadro de mando** se **desnormaliza** (rendimiento de lectura). *(§1.13, §2.13)*

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Propone índices B-tree adecuados y reconoce su coste en escritura | 3 |
| Identifica EXPLAIN y la necesidad de estadísticas | 2 |
| Aplica particionamiento por rango con *partition pruning* | 2 |
| Justifica la desnormalización/vista materializada y distingue OLTP vs OLAP | 3 |

---

*Los tres casos pueden resolverse íntegramente con el contenido teórico del tema. Las referencias entre paréntesis (§) remiten a `tema-17-contenido.md`.*
