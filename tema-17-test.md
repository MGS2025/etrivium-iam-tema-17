# Tema 17 — Test de Autoevaluación

> **Título**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-06-20
> **Fuentes**: ver tema-17-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: Diseño y niveles (P1-P8), E-R y transformación (P9-P18), Integridad/DDL/físico (P19-P30), Modelo relacional y claves (P31-P40), Álgebra y cálculo (P41-P47), Normalización (P48-P60).

---

### Pregunta 1

**¿Cuál es el orden correcto de los tres niveles de diseño de una base de datos?**

A) Físico → lógico → conceptual
B) Conceptual → lógico → físico
C) Lógico → conceptual → físico

<details><summary>Respuesta</summary>

**Correcta: B) Conceptual → lógico → físico** Se va de lo más abstracto (independiente del SGBD) a lo más concreto (producto y almacenamiento).

*Referencia: §1.2 [ELMASRI]*
</details>

---

### Pregunta 2

**El diseño conceptual de una base de datos se caracteriza por ser:**

A) Una descripción de los ficheros físicos en disco
B) Dependiente del producto concreto (Oracle, PostgreSQL)
C) Independiente de cualquier SGBD

<details><summary>Respuesta</summary>

**Correcta: C) Independiente de cualquier SGBD** El modelo conceptual (típicamente E-R) describe la realidad sin atarse a ninguna tecnología.

*Referencia: §1.2 [ELMASRI]*
</details>

---

### Pregunta 3

**¿Qué permite la independencia física de datos?**

A) Cambiar el nombre de las entidades sin más
B) Eliminar las claves primarias
C) Modificar el almacenamiento (índices, ficheros) sin alterar el esquema lógico ni las aplicaciones

<details><summary>Respuesta</summary>

**Correcta: C) Modificar el almacenamiento (índices, ficheros) sin alterar el esquema lógico ni las aplicaciones** Es la independencia más fácil de conseguir gracias a la separación en niveles.

*Referencia: §1.3 [DATE]*
</details>

---

### Pregunta 4

**¿Cuál NO es un objetivo del diseño de bases de datos?**

A) Mínima redundancia controlada
B) Maximizar deliberadamente la duplicación de datos
C) Integridad de los datos

<details><summary>Respuesta</summary>

**Correcta: B) Maximizar deliberadamente la duplicación de datos** La redundancia no controlada provoca anomalías; el diseño busca minimizarla.

*Referencia: §1.3 [ELMASRI]*
</details>

---

### Pregunta 5

**El diseño lógico de una base de datos relacional produce:**

A) El conjunto de tablas con sus claves, normalizadas, independiente del producto
B) El diagrama de despliegue de servidores
C) El código fuente de la aplicación cliente

<details><summary>Respuesta</summary>

**Correcta: A) El conjunto de tablas con sus claves, normalizadas, independiente del producto** Transforma el modelo conceptual en el modelo del tipo de SGBD elegido (relacional).

*Referencia: §2.1 [ELMASRI]*
</details>

---

### Pregunta 6

**La independencia lógica de datos se apoya principalmente en:**

A) Los índices bitmap
B) El particionamiento por rango
C) Las vistas

<details><summary>Respuesta</summary>

**Correcta: C) Las vistas** Las vistas permiten cambiar el esquema lógico afectando lo mínimo a las aplicaciones que consultan a través de ellas.

*Referencia: §1.3 [DATE]*
</details>

---

### Pregunta 7

**¿A qué nivel de diseño corresponde decidir el particionamiento de una tabla y sus índices?**

A) Diseño conceptual
B) Diseño físico
C) Análisis de requisitos

<details><summary>Respuesta</summary>

**Correcta: B) Diseño físico** El diseño físico decide el almacenamiento y las estructuras de acceso en el producto concreto.

*Referencia: §2.6 [RAMAKRISHNAN]*
</details>

---

### Pregunta 8

**La arquitectura ANSI/SPARC de tres esquemas se relaciona con el diseño en niveles en que:**

A) El esquema interno equivale al diseño físico y los esquemas externos a las vistas
B) Solo define un único esquema global
C) Sustituye al modelo relacional

<details><summary>Respuesta</summary>

**Correcta: A) El esquema interno equivale al diseño físico y los esquemas externos a las vistas** Interno↔físico, conceptual↔lógico, externos↔vistas de usuario.

*Referencia: §1.2 [SILBER]*
</details>

---

### Pregunta 9

**En el modelo entidad-relación, una entidad se representa gráficamente con:**

A) Un rombo
B) Una elipse
C) Un rectángulo

<details><summary>Respuesta</summary>

**Correcta: C) Un rectángulo** El rombo es la relación y la elipse el atributo.

*Referencia: §1.4 [CHEN76]*
</details>

---

### Pregunta 10

**¿Qué representa un rombo en un diagrama E-R?**

A) Una relación (interrelación) entre entidades
B) Un atributo
C) Una clave primaria

<details><summary>Respuesta</summary>

**Correcta: A) Una relación (interrelación) entre entidades** El rombo une dos o más entidades; la cardinalidad se anota en las líneas.

*Referencia: §1.4 [CHEN76]*
</details>

---

### Pregunta 11

**Una relación 1:N entre DISTRITO y HABITANTE se transforma en el modelo relacional:**

A) Creando una tabla intermedia con dos claves ajenas
B) Propagando la clave de DISTRITO como clave ajena en HABITANTE
C) Fusionando ambas entidades en una sola tabla siempre

<details><summary>Respuesta</summary>

**Correcta: B) Propagando la clave de DISTRITO como clave ajena en HABITANTE** En 1:N la clave del lado «1» va al lado «N»; no se crea tabla nueva.

*Referencia: §2.2 [ELMASRI]*
</details>

---

### Pregunta 12

**Una relación N:M entre HABITANTE y TRIBUTO se transforma:**

A) Propagando la clave de uno en el otro
B) Sin cambios en el esquema
C) Creando una tabla intermedia con clave compuesta y dos claves ajenas

<details><summary>Respuesta</summary>

**Correcta: C) Creando una tabla intermedia con clave compuesta y dos claves ajenas** La tabla puente almacena además los atributos propios de la relación (p. ej. porcentaje de titularidad).

*Referencia: §2.2 [ELMASRI]*
</details>

---

### Pregunta 13

**Un atributo multivaluado (p. ej. varios teléfonos de un habitante) se transforma en:**

A) Una tabla aparte relacionada por clave ajena
B) Una columna que contiene la lista separada por comas
C) Tres columnas fijas: telefono1, telefono2, telefono3

<details><summary>Respuesta</summary>

**Correcta: A) Una tabla aparte relacionada por clave ajena** Guardar varios valores en una celda violaría la 1FN; las columnas fijas limitan artificialmente el número.

*Referencia: §2.2 [ELMASRI]*
</details>

---

### Pregunta 14

**¿Qué es una entidad débil?**

A) Una entidad con muchos atributos
B) Una entidad que no participa en ninguna relación
C) Una entidad sin clave propia que depende de otra entidad fuerte

<details><summary>Respuesta</summary>

**Correcta: C) Una entidad sin clave propia que depende de otra entidad fuerte** Su clave primaria incluye la clave de la entidad fuerte de la que depende.

*Referencia: §1.4 [ELMASRI]*
</details>

---

### Pregunta 15

**La participación total de una entidad en una relación significa que:**

A) La relación es siempre N:M
B) La entidad tiene varios atributos clave
C) Toda ocurrencia de la entidad debe participar en la relación

<details><summary>Respuesta</summary>

**Correcta: C) Toda ocurrencia de la entidad debe participar en la relación** En el modelo lógico se traduce en una clave ajena NOT NULL.

*Referencia: §1.4 [ELMASRI]*
</details>

---

### Pregunta 16

**Un atributo derivado (como la edad a partir de la fecha de nacimiento):**

A) En principio no se almacena, se calcula
B) Debe ser siempre clave primaria
C) Obliga a crear una tabla intermedia

<details><summary>Respuesta</summary>

**Correcta: A) En principio no se almacena, se calcula** Almacenarlo introduce redundancia; solo se hace por desnormalización justificada.

*Referencia: §2.2 [ELMASRI]*
</details>

---

### Pregunta 17

**Una relación recursiva (reflexiva) es aquella en la que:**

A) Una entidad se relaciona consigo misma
B) Participan exactamente tres entidades
C) No hay cardinalidad definida

<details><summary>Respuesta</summary>

**Correcta: A) Una entidad se relaciona consigo misma** Ejemplo: un EMPLEADO «es jefe de» otro EMPLEADO.

*Referencia: §1.4 [ELMASRI]*
</details>

---

### Pregunta 18

**Una clave subrogada (surrogate) es:**

A) Una clave ajena que admite nulos
B) Un identificador artificial sin significado de negocio (p. ej. autonumérico)
C) Una clave formada por todos los atributos de la tabla

<details><summary>Respuesta</summary>

**Correcta: B) Un identificador artificial sin significado de negocio (p. ej. autonumérico)** Aporta estabilidad frente a las claves naturales, que pueden cambiar.

*Referencia: §2.5 [DATE]*
</details>

---

### Pregunta 19

**La integridad de entidad establece que:**

A) Las claves ajenas no pueden existir
B) Toda tabla debe tener al menos 100 filas
C) Ningún atributo de la clave primaria puede ser nulo

<details><summary>Respuesta</summary>

**Correcta: C) Ningún atributo de la clave primaria puede ser nulo** Si lo fuera, no podría identificar unívocamente la fila.

*Referencia: §2.4 [CODD70]*
</details>

---

### Pregunta 20

**La integridad referencial exige que el valor de una clave ajena:**

A) Coincida con un valor existente de la clave primaria referenciada o sea nulo
B) Sea siempre distinto al de la clave primaria
C) Sea único en toda la base de datos

<details><summary>Respuesta</summary>

**Correcta: A) Coincida con un valor existente de la clave primaria referenciada o sea nulo** Evita las «referencias colgantes».

*Referencia: §2.4 [DATE]*
</details>

---

### Pregunta 21

**¿Qué política referencial borra automáticamente las filas hijas al borrar la fila padre?**

A) NO ACTION / RESTRICT
B) CASCADE
C) SET DEFAULT

<details><summary>Respuesta</summary>

**Correcta: B) CASCADE** Propaga el borrado o la actualización a las filas que referencian la fila padre.

*Referencia: §2.4 [ISO9075]*
</details>

---

### Pregunta 22

**¿A qué sublenguaje de SQL pertenece la sentencia CREATE TABLE?**

A) DML
B) DCL
C) DDL

<details><summary>Respuesta</summary>

**Correcta: C) DDL** El DDL (Data Definition Language) define la estructura: tablas, índices, vistas y restricciones.

*Referencia: §2.5 [ISO9075]*
</details>

---

### Pregunta 23

**Las sentencias GRANT y REVOKE pertenecen a:**

A) DCL (control de acceso/permisos)
B) DML
C) TCL

<details><summary>Respuesta</summary>

**Correcta: A) DCL (control de acceso/permisos)** El DCL controla los privilegios de usuarios y roles.

*Referencia: §2.5 [ISO9075]*
</details>

---

### Pregunta 24

**¿Cuál de estas afirmaciones sobre DELETE y TRUNCATE es correcta?**

A) Ambas son DML y soportan WHERE
B) TRUNCATE permite borrar filas concretas con WHERE
C) DELETE es DML (transaccional, con WHERE) y TRUNCATE es DDL (vacía la tabla)

<details><summary>Respuesta</summary>

**Correcta: C) DELETE es DML (transaccional, con WHERE) y TRUNCATE es DDL (vacía la tabla)** TRUNCATE es rápida y normalmente no transaccional ni filtrable.

*Referencia: §2.5 [ISO9075]*
</details>

---

### Pregunta 25

**Un índice de tipo hash es adecuado para:**

A) Búsquedas por rango (BETWEEN, <, >)
B) Búsquedas por igualdad exacta
C) Ordenar el resultado con ORDER BY

<details><summary>Respuesta</summary>

**Correcta: B) Búsquedas por igualdad exacta** El hash no soporta rangos ni orden; para eso se usa el B+tree.

*Referencia: §2.8 [RAMAKRISHNAN]*
</details>

---

### Pregunta 26

**¿Qué ventaja tiene el índice B+tree que no tiene el hash?**

A) Sirve para búsquedas por igualdad y también por rango y orden
B) Ocupa menos espacio siempre
C) No necesita mantenerse al insertar

<details><summary>Respuesta</summary>

**Correcta: A) Sirve para búsquedas por igualdad y también por rango y orden** Sus hojas están al mismo nivel y enlazadas, lo que facilita los recorridos por rango.

*Referencia: §2.8 [RAMAKRISHNAN]*
</details>

---

### Pregunta 27

**Crear muchos índices sobre una tabla:**

A) Siempre mejora el rendimiento global
B) No tiene ningún efecto secundario
C) Acelera lecturas pero penaliza escrituras y consume espacio

<details><summary>Respuesta</summary>

**Correcta: C) Acelera lecturas pero penaliza escrituras y consume espacio** Cada índice debe mantenerse en cada INSERT/UPDATE/DELETE.

*Referencia: §2.8 [RAMAKRISHNAN]*
</details>

---

### Pregunta 28

**El índice bitmap es especialmente eficiente en columnas:**

A) De muy alta cardinalidad (como el DNI)
B) De baja cardinalidad (como el sexo o el distrito) en entornos analíticos
C) De tipo BLOB

<details><summary>Respuesta</summary>

**Correcta: B) De baja cardinalidad (como el sexo o el distrito) en entornos analíticos** Penaliza la concurrencia de escrituras, por eso es típico de OLAP.

*Referencia: §2.8 [ORA-CONCEPTS]*
</details>

---

### Pregunta 29

**Un índice agrupado (clustered):**

A) Puede haber tantos como se quiera por tabla
B) Determina el orden físico de las filas y solo puede haber uno por tabla
C) No tiene relación con el orden de las filas

<details><summary>Respuesta</summary>

**Correcta: B) Determina el orden físico de las filas y solo puede haber uno por tabla** A menudo coincide con la clave primaria.

*Referencia: §2.8 [MS-SQL-INDEX]*
</details>

---

### Pregunta 30

**El plan de ejecución de una consulta es:**

A) La ruta de operaciones físicas que el optimizador elige para resolverla
B) El texto literal de la sentencia SQL
C) La lista de usuarios con permiso sobre la tabla

<details><summary>Respuesta</summary>

**Correcta: A) La ruta de operaciones físicas que el optimizador elige para resolverla** Se inspecciona con EXPLAIN y depende de las estadísticas.

*Referencia: §2.9 [SILBER]*
</details>

---

### Pregunta 31

**En el modelo relacional, el grado de una relación es:**

A) El número de tuplas (filas)
B) El número de atributos (columnas)
C) El número de claves ajenas

<details><summary>Respuesta</summary>

**Correcta: B) El número de atributos (columnas)** La cardinalidad, en cambio, es el número de filas.

*Referencia: §3.1 [DATE]*
</details>

---

### Pregunta 32

**La cardinalidad de una relación se refiere a:**

A) El número de tuplas (filas)
B) El número de columnas
C) El número de dominios definidos

<details><summary>Respuesta</summary>

**Correcta: A) El número de tuplas (filas)** Grado = columnas; cardinalidad = filas.

*Referencia: §3.1 [DATE]*
</details>

---

### Pregunta 33

**El dominio de un atributo es:**

A) El nombre de la tabla
B) La clave primaria de la relación
C) El conjunto de valores válidos que puede tomar el atributo

<details><summary>Respuesta</summary>

**Correcta: C) El conjunto de valores válidos que puede tomar el atributo** Por ejemplo, el dominio de «distrito» son los códigos 1..21.

*Referencia: §3.1 [DATE]*
</details>

---

### Pregunta 34

**¿Qué diferencia hay entre una relación teórica y una tabla SQL?**

A) Ninguna, son idénticas
B) La tabla SQL no admite claves
C) La relación teórica es un conjunto (sin duplicados); la tabla SQL es un multiconjunto (permite filas repetidas salvo restricción)

<details><summary>Respuesta</summary>

**Correcta: C) La relación teórica es un conjunto (sin duplicados); la tabla SQL es un multiconjunto (permite filas repetidas salvo restricción)** Por eso SELECT puede devolver duplicados salvo DISTINCT.

*Referencia: §3.1 [DATE]*
</details>

---

### Pregunta 35

**Una superclave es:**

A) Un conjunto de atributos que identifica unívocamente una tupla (puede no ser mínimo)
B) Siempre un único atributo
C) Una clave que apunta a otra tabla

<details><summary>Respuesta</summary>

**Correcta: A) Un conjunto de atributos que identifica unívocamente una tupla (puede no ser mínimo)** La clave candidata es la superclave mínima.

*Referencia: §3.2 [DATE]*
</details>

---

### Pregunta 36

**Una clave candidata es:**

A) Cualquier columna de la tabla
B) Una superclave mínima (si se le quita un atributo deja de identificar)
C) La clave que se descarta del diseño

<details><summary>Respuesta</summary>

**Correcta: B) Una superclave mínima (si se le quita un atributo deja de identificar)** De entre las candidatas, la elegida es la primaria; las demás, alternativas.

*Referencia: §3.2 [ELMASRI]*
</details>

---

### Pregunta 37

**Las claves candidatas no elegidas como primaria se denominan:**

A) Claves alternativas
B) Claves ajenas
C) Superclaves

<details><summary>Respuesta</summary>

**Correcta: A) Claves alternativas** Suelen implementarse con una restricción UNIQUE.

*Referencia: §3.2 [DATE]*
</details>

---

### Pregunta 38

**En la relación HABITANTE(dni, nss, nombre), si elegimos dni como primaria, el NSS es:**

A) Una clave ajena
B) Un atributo no clave cualquiera
C) Una clave alternativa (candidata no elegida)

<details><summary>Respuesta</summary>

**Correcta: C) Una clave alternativa (candidata no elegida)** El NSS también identifica unívocamente, pero no fue elegido como primaria.

*Referencia: §3.2 [DATE]*
</details>

---

### Pregunta 39

**El valor NULL en el modelo relacional representa:**

A) El número cero
B) Información ausente o desconocida
C) Una cadena vacía

<details><summary>Respuesta</summary>

**Correcta: B) Información ausente o desconocida** No es cero ni cadena vacía, e introduce una lógica de tres valores.

*Referencia: §3.3 [DATE]*
</details>

---

### Pregunta 40

**¿Cuál de estas es una regla de integridad del modelo relacional?**

A) Toda tabla debe tener exactamente una clave ajena
B) Los nombres de columna deben ir en mayúsculas
C) La integridad referencial: toda clave ajena referencia una fila existente o es nula

<details><summary>Respuesta</summary>

**Correcta: C) La integridad referencial: toda clave ajena referencia una fila existente o es nula** Junto con la integridad de entidad, de dominio y las reglas de negocio.

*Referencia: §3.3 [CODD70]*
</details>

---

### Pregunta 41

**El álgebra relacional es un lenguaje:**

A) Procedimental (indica cómo obtener el resultado paso a paso)
B) Declarativo puro (solo indica qué se quiere)
C) De definición de estructura (DDL)

<details><summary>Respuesta</summary>

**Correcta: A) Procedimental (indica cómo obtener el resultado paso a paso)** El cálculo relacional, en cambio, es declarativo.

*Referencia: §3.4 [DATE]*
</details>

---

### Pregunta 42

**La operación de selección (σ) del álgebra relacional:**

A) Elige columnas
B) Filtra las filas que cumplen una condición
C) Une dos tablas

<details><summary>Respuesta</summary>

**Correcta: B) Filtra las filas que cumplen una condición** La proyección (π) es la que elige columnas.

*Referencia: §3.4 [ELMASRI]*
</details>

---

### Pregunta 43

**La operación de proyección (π) del álgebra relacional:**

A) Selecciona columnas (atributos), eliminando duplicados
B) Filtra filas según una condición
C) Calcula el producto cartesiano

<details><summary>Respuesta</summary>

**Correcta: A) Selecciona columnas (atributos), eliminando duplicados** No confundir con la selección σ, que filtra filas.

*Referencia: §3.4 [ELMASRI]*
</details>

---

### Pregunta 44

**¿Cuáles son los cinco operadores primitivos del álgebra relacional?**

A) Join, intersección, división, unión y selección
B) Selección, proyección, unión, diferencia y producto cartesiano
C) Selección, proyección, join, división y renombrado

<details><summary>Respuesta</summary>

**Correcta: B) Selección, proyección, unión, diferencia y producto cartesiano** El join, la intersección y la división se derivan de estos cinco.

*Referencia: §3.4 [CODD70]*
</details>

---

### Pregunta 45

**La operación de división (÷) resuelve consultas del tipo:**

A) «cuántas filas tiene la tabla»
B) «cuál es el valor máximo de una columna»
C) «qué elementos están relacionados con TODOS los de otro conjunto»

<details><summary>Respuesta</summary>

**Correcta: C) «qué elementos están relacionados con TODOS los de otro conjunto»** Por ejemplo, qué habitantes han pagado todos los tributos obligatorios.

*Referencia: §3.4 [DATE]*
</details>

---

### Pregunta 46

**El cálculo relacional es un lenguaje:**

A) Declarativo (describe qué se quiere, no cómo obtenerlo)
B) Procedimental
C) De control de transacciones

<details><summary>Respuesta</summary>

**Correcta: A) Declarativo (describe qué se quiere, no cómo obtenerlo)** Tiene dos variantes: de tuplas y de dominios.

*Referencia: §3.5 [DATE]*
</details>

---

### Pregunta 47

**Respecto al poder expresivo, el álgebra relacional y el cálculo relacional:**

A) El álgebra es más potente que el cálculo
B) El cálculo es más potente que el álgebra
C) Son equivalentes (mismo poder expresivo)

<details><summary>Respuesta</summary>

**Correcta: C) Son equivalentes (mismo poder expresivo)** Es el teorema de equivalencia de Codd; SQL se inspira en ambos.

*Referencia: §3.5 [DATE]*
</details>

---

### Pregunta 48

**La normalización tiene como objetivo principal:**

A) Aumentar la velocidad de todas las consultas
B) Eliminar la redundancia y las anomalías de actualización
C) Reducir el número de tablas al mínimo

<details><summary>Respuesta</summary>

**Correcta: B) Eliminar la redundancia y las anomalías de actualización** Se basa en el análisis de las dependencias funcionales.

*Referencia: §4.1 [CODD72]*
</details>

---

### Pregunta 49

**¿Cuáles son las tres anomalías que provoca un mal diseño?**

A) De compilación, de ejecución y de sintaxis
B) De inserción, de borrado y de actualización
C) De red, de disco y de memoria

<details><summary>Respuesta</summary>

**Correcta: B) De inserción, de borrado y de actualización** Las tres derivan de la redundancia de datos.

*Referencia: §4.1 [ELMASRI]*
</details>

---

### Pregunta 50

**Una dependencia funcional X → Y significa que:**

A) Y siempre es mayor que X
B) X e Y son claves ajenas
C) El valor de X determina unívocamente el valor de Y

<details><summary>Respuesta</summary>

**Correcta: C) El valor de X determina unívocamente el valor de Y** X es el determinante; dos tuplas con igual X tienen igual Y.

*Referencia: §4.2 [ELMASRI]*
</details>

---

### Pregunta 51

**¿Cuáles son los tres axiomas de Armstrong?**

A) Reflexividad, aumento y transitividad
B) Unión, descomposición y pseudotransitividad
C) Inserción, borrado y actualización

<details><summary>Respuesta</summary>

**Correcta: A) Reflexividad, aumento y transitividad** Son correctos y completos; las demás reglas se derivan de ellos.

*Referencia: §4.2 [ARMSTRONG74]*
</details>

---

### Pregunta 52

**El cierre de atributos X⁺ sirve para:**

A) Ordenar las filas de una tabla
B) Determinar si X es superclave y hallar las claves candidatas
C) Calcular el tamaño físico de la tabla

<details><summary>Respuesta</summary>

**Correcta: B) Determinar si X es superclave y hallar las claves candidatas** Si X⁺ contiene todos los atributos, X es superclave.

*Referencia: §4.2 [ELMASRI]*
</details>

---

### Pregunta 53

**Una relación está en Primera Forma Normal (1FN) cuando:**

A) No tiene claves ajenas
B) Todos sus atributos son atómicos (un solo valor por celda)
C) Tiene menos de cinco columnas

<details><summary>Respuesta</summary>

**Correcta: B) Todos sus atributos son atómicos (un solo valor por celda)** Sin grupos repetitivos ni valores multivaluados.

*Referencia: §4.3 [CODD70]*
</details>

---

### Pregunta 54

**La Segunda Forma Normal (2FN) elimina:**

A) Las dependencias transitivas
B) Las dependencias multivaluadas
C) Las dependencias funcionales parciales de la clave

<details><summary>Respuesta</summary>

**Correcta: C) Las dependencias funcionales parciales de la clave** Solo tiene riesgo cuando la clave primaria es compuesta.

*Referencia: §4.4 [CODD72]*
</details>

---

### Pregunta 55

**Si la clave primaria de una relación en 1FN es un único atributo, entonces:**

A) Está automáticamente en 2FN
B) Nunca puede estar en 3FN
C) No puede tener claves ajenas

<details><summary>Respuesta</summary>

**Correcta: A) Está automáticamente en 2FN** Sin clave compuesta no puede haber dependencias parciales.

*Referencia: §4.4 [CODD72]*
</details>

---

### Pregunta 56

**La Tercera Forma Normal (3FN) exige que no haya:**

A) Dependencias transitivas entre atributos no clave
B) Claves primarias
C) Valores nulos en ninguna columna

<details><summary>Respuesta</summary>

**Correcta: A) Dependencias transitivas entre atributos no clave** Mnemotecnia: cada atributo depende de la clave, toda la clave y nada más que la clave.

*Referencia: §4.5 [CODD72]*
</details>

---

### Pregunta 57

**La Forma Normal de Boyce-Codd (BCNF) exige que:**

A) Toda tabla tenga clave subrogada
B) Todo determinante de una dependencia funcional no trivial sea clave candidata
C) No existan claves ajenas

<details><summary>Respuesta</summary>

**Correcta: B) Todo determinante de una dependencia funcional no trivial sea clave candidata** Es una 3FN reforzada; toda relación en BCNF está en 3FN.

*Referencia: §4.6 [CODD74BCNF]*
</details>

---

### Pregunta 58

**¿Qué propiedad de una descomposición es obligatoria?**

A) Que aumente el número de tablas
B) La descomposición sin pérdida de información (lossless join)
C) Que elimine todas las claves ajenas

<details><summary>Respuesta</summary>

**Correcta: B) La descomposición sin pérdida de información (lossless join)** Se garantiza si el atributo común es clave de al menos una de las tablas resultantes.

*Referencia: §4.6 [SILBER]*
</details>

---

### Pregunta 59

**La Cuarta Forma Normal (4FN) trata las dependencias:**

A) Funcionales parciales
B) Transitivas
C) Multivaluadas

<details><summary>Respuesta</summary>

**Correcta: C) Multivaluadas** La 5FN, por su parte, trata las dependencias de reunión (join).

*Referencia: §4.7 [FAGIN77]*
</details>

---

### Pregunta 60

**La desnormalización controlada consiste en:**

A) Reintroducir redundancia de forma deliberada para mejorar el rendimiento, asumiendo el coste de mantener la coherencia
B) Eliminar todas las claves primarias
C) Volver siempre a la 1FN

<details><summary>Respuesta</summary>

**Correcta: A) Reintroducir redundancia de forma deliberada para mejorar el rendimiento, asumiendo el coste de mantener la coherencia** Se aplica al final, sobre cuellos de botella medidos, típica en entornos OLAP.

*Referencia: §4.8 [RAMAKRISHNAN]*
</details>
