# Tema 17 — Catálogo de Diagramas

> **Título oficial**: Diseño de bases de datos. Diseño lógico y físico. El modelo lógico relacional. Normalización.
>
> **Versión**: v1.0
> **Fecha**: 2026-06-20
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Los tres niveles de diseño | §1.2 | Flujo | 660×300 |
| D2 | Elementos del modelo entidad-relación | §1.4 | Conceptual | 660×320 |
| D3 | Transformación E-R → relacional | §2.2 | Comparativa | 680×320 |
| D4 | Integridad de entidad y referencial | §2.4 | Estructura | 680×300 |
| D5 | Los cuatro sublenguajes de SQL | §2.5 | Bloques | 660×300 |
| D6 | Tipos de índice | §2.8 | Comparativa | 680×320 |
| D7 | Conceptos del modelo relacional | §3.1 | Estructura | 680×320 |
| D8 | Tipos de claves | §3.2 | Anidamiento | 620×340 |
| D9 | Operadores del álgebra relacional | §3.4 | Mapa | 680×340 |
| D10 | Las tres anomalías | §4.1 | Conceptual | 660×300 |
| D11 | Las formas normales (anidadas) | §4.1-2.12 | Anidamiento | 640×360 |
| D12 | Estructura de un índice B+tree | §2.8 | Árbol | 680×320 |

---

## D1 · Los tres niveles de diseño

**Sección**: §1.2 — Los tres niveles de diseño y el ciclo de vida
**Propósito**: Mostrar la secuencia conceptual → lógico → físico y de qué depende cada nivel.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Los tres niveles del diseño de bases de datos: conceptual, lógico y físico, del más abstracto al más concreto">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="330" y="28" text-anchor="middle" class="h">Del análisis de requisitos a la base de datos</text>
  <rect x="120" y="48" width="420" height="56" rx="6" fill="#6ea3d2"/><text x="330" y="72" text-anchor="middle" class="t">1 · Diseño CONCEPTUAL</text><text x="330" y="92" text-anchor="middle" class="s">Modelo entidad-relación · independiente del SGBD</text>
  <rect x="120" y="120" width="420" height="56" rx="6" fill="#0055a0"/><text x="330" y="144" text-anchor="middle" class="t">2 · Diseño LÓGICO</text><text x="330" y="164" text-anchor="middle" class="s">Tablas, claves y normalización · depende del modelo relacional</text>
  <rect x="120" y="192" width="420" height="56" rx="6" fill="#003d73"/><text x="330" y="216" text-anchor="middle" class="t">3 · Diseño FÍSICO</text><text x="330" y="236" text-anchor="middle" class="s">Ficheros, índices, particiones · depende del producto concreto</text>
  <path d="M330 104 L330 118" stroke="#888" stroke-width="2" marker-end="url(#a)"/>
  <path d="M330 176 L330 190" stroke="#888" stroke-width="2" marker-end="url(#a)"/>
  <defs><marker id="a" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#888"/></marker></defs>
  <text x="40" y="76" class="l">+ abstracto</text>
  <text x="40" y="220" class="l">+ concreto</text>
  <text x="650" y="290" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ELMASRI, cap. 3]</text>
</svg>
```

---

## D2 · Elementos del modelo entidad-relación

**Sección**: §1.4 — Diseño conceptual: el modelo entidad-relación
**Propósito**: Recordar la notación E-R (rectángulo, elipse, rombo) con un ejemplo del Padrón.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 320" role="img" aria-label="Elementos del modelo entidad-relación: entidad rectángulo, atributo elipse, relación rombo, con ejemplo Habitante reside en Distrito">
  <style>.b{font:600 12px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="330" y="26" text-anchor="middle" class="h">Notación E-R (ejemplo: Padrón Municipal)</text>
  <rect x="60" y="120" width="130" height="50" rx="4" fill="#0055a0"/><text x="125" y="150" text-anchor="middle" class="b">HABITANTE</text>
  <rect x="470" y="120" width="130" height="50" rx="4" fill="#0055a0"/><text x="535" y="150" text-anchor="middle" class="b">DISTRITO</text>
  <polygon points="330,120 390,145 330,170 270,145" fill="#e89822"/><text x="330" y="149" text-anchor="middle" class="b">reside</text>
  <line x1="190" y1="145" x2="270" y2="145" stroke="#444" stroke-width="1.5"/><text x="225" y="138" text-anchor="middle" class="l">N</text>
  <line x1="390" y1="145" x2="470" y2="145" stroke="#444" stroke-width="1.5"/><text x="435" y="138" text-anchor="middle" class="l">1</text>
  <ellipse cx="90" cy="70" rx="44" ry="22" fill="#6ea3d2"/><text x="90" y="74" text-anchor="middle" class="b">dni (PK)</text>
  <ellipse cx="170" cy="55" rx="40" ry="22" fill="#6ea3d2"/><text x="170" y="59" text-anchor="middle" class="b">nombre</text>
  <line x1="100" y1="90" x2="118" y2="120" stroke="#888"/><line x1="165" y1="76" x2="135" y2="120" stroke="#888"/>
  <ellipse cx="535" cy="70" rx="46" ry="22" fill="#6ea3d2"/><text x="535" y="74" text-anchor="middle" class="b">codigo (PK)</text>
  <line x1="535" y1="92" x2="535" y2="120" stroke="#888"/>
  <text x="60" y="230" class="l">▭ Entidad   ◇ Relación   ◯ Atributo   — Cardinalidad (1:1, 1:N, N:M)</text>
  <text x="60" y="252" class="l">«Un distrito tiene N habitantes; un habitante reside en 1 distrito» → relación 1:N</text>
  <text x="650" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CHEN76]</text>
</svg>
```

---

## D3 · Transformación E-R → relacional

**Sección**: §2.2 — Transformación de entidades y relaciones al modelo relacional
**Propósito**: Contrastar la regla 1:N (propaga clave) con la N:M (crea tabla intermedia).

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Reglas de transformación: una relación 1 a N propaga la clave ajena; una relación N a M crea una tabla intermedia con dos claves ajenas">
  <style>.b{font:600 11px system-ui,sans-serif;fill:#fff}.c{font:600 11px system-ui,sans-serif;fill:#0055a0}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 12px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="170" y="26" text-anchor="middle" class="h">Relación 1:N → propaga clave</text>
  <rect x="40" y="48" width="110" height="44" rx="4" fill="#0055a0"/><text x="95" y="66" text-anchor="middle" class="b">DISTRITO</text><text x="95" y="82" text-anchor="middle" class="b">codigo (PK)</text>
  <rect x="190" y="48" width="130" height="44" rx="4" fill="#2d8659"/><text x="255" y="66" text-anchor="middle" class="b">HABITANTE</text><text x="255" y="82" text-anchor="middle" class="b">dni (PK), cod_distrito (FK)</text>
  <path d="M150 70 L190 70" stroke="#888" stroke-width="2" marker-end="url(#b)"/>
  <text x="95" y="120" text-anchor="middle" class="l">No se crea tabla;</text><text x="95" y="136" text-anchor="middle" class="l">la clave va al lado «N»</text>
  <text x="510" y="26" text-anchor="middle" class="h">Relación N:M → tabla intermedia</text>
  <rect x="370" y="48" width="110" height="44" rx="4" fill="#0055a0"/><text x="425" y="66" text-anchor="middle" class="b">HABITANTE</text><text x="425" y="82" text-anchor="middle" class="b">dni (PK)</text>
  <rect x="560" y="48" width="100" height="44" rx="4" fill="#0055a0"/><text x="610" y="66" text-anchor="middle" class="b">TRIBUTO</text><text x="610" y="82" text-anchor="middle" class="b">id (PK)</text>
  <rect x="440" y="150" width="170" height="58" rx="4" fill="#d13c3c"/><text x="525" y="172" text-anchor="middle" class="b">TITULARIDAD</text><text x="525" y="188" text-anchor="middle" class="b">dni (FK), id (FK)</text><text x="525" y="202" text-anchor="middle" class="b">PK(dni, id) + porcentaje</text>
  <path d="M425 92 L500 148" stroke="#888" stroke-width="2"/><path d="M610 92 L555 148" stroke="#888" stroke-width="2"/>
  <text x="525" y="232" text-anchor="middle" class="l">Clave compuesta + 2 claves ajenas + atributos propios</text>
  <defs><marker id="b" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#888"/></marker></defs>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ELMASRI, cap. 9]</text>
</svg>
```

---

## D4 · Integridad de entidad y referencial

**Sección**: §2.4 — Integridad de entidad e integridad referencial
**Propósito**: Visualizar la clave primaria (sin nulos) y la clave ajena que apunta a una fila existente.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Integridad de entidad: la clave primaria no es nula; integridad referencial: la clave ajena apunta a una fila existente de la tabla referenciada">
  <style>.b{font:600 11px system-ui,sans-serif;fill:#fff}.k{font:700 11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 12px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="120" y="26" text-anchor="middle" class="h">HABITANTE</text>
  <rect x="40" y="40" width="160" height="26" fill="#0055a0"/><text x="60" y="58" class="k">dni (PK)</text><text x="130" y="58" class="k">cod_distrito (FK)</text>
  <rect x="40" y="66" width="160" height="24" fill="#e8f0f8"/><text x="60" y="83" class="l">0001A</text><text x="150" y="83" class="l">1</text>
  <rect x="40" y="90" width="160" height="24" fill="#fff"/><text x="60" y="107" class="l">0002B</text><text x="150" y="107" class="l">2</text>
  <rect x="40" y="114" width="160" height="24" fill="#fbeeed"/><text x="58" y="131" class="l">(nulo)</text><text x="150" y="131" class="l">1</text>
  <text x="120" y="160" text-anchor="middle" fill="#d13c3c" font="700 11px system-ui,sans-serif">✗ PK nula → viola integridad de entidad</text>
  <text x="500" y="26" text-anchor="middle" class="h">DISTRITO</text>
  <rect x="430" y="40" width="160" height="26" fill="#2d8659"/><text x="450" y="58" class="k">codigo (PK)</text><text x="535" y="58" class="k">nombre</text>
  <rect x="430" y="66" width="160" height="24" fill="#e8f5ee"/><text x="450" y="83" class="l">1</text><text x="530" y="83" class="l">Centro</text>
  <rect x="430" y="90" width="160" height="24" fill="#fff"/><text x="450" y="107" class="l">2</text><text x="530" y="107" class="l">Arganzuela</text>
  <path d="M200 78 C320 78 320 78 428 78" stroke="#2d8659" stroke-width="2" fill="none" marker-end="url(#c)"/>
  <text x="315" y="72" text-anchor="middle" class="l">FK → PK existente ✓</text>
  <text x="430" y="160" class="l">Integridad referencial: toda FK apunta a una fila real o es nula</text>
  <defs><marker id="c" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#2d8659"/></marker></defs>
  <text x="670" y="288" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CODD70; DATE, cap. 9]</text>
</svg>
```

---

## D5 · Los cuatro sublenguajes de SQL

**Sección**: §2.5 — Lenguajes de definición y manipulación
**Propósito**: Separar DDL / DML / DCL / TCL por su finalidad.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Los cuatro sublenguajes de SQL: DDL para la estructura, DML para los datos, DCL para los permisos y TCL para las transacciones">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="330" y="28" text-anchor="middle" class="h">SQL (ISO/IEC 9075) — cuatro sublenguajes</text>
  <rect x="40" y="50" width="280" height="90" rx="6" fill="#0055a0"/><text x="180" y="78" text-anchor="middle" class="t">DDL — Estructura</text><text x="180" y="100" text-anchor="middle" class="s">CREATE · ALTER · DROP · TRUNCATE</text><text x="180" y="120" text-anchor="middle" class="s">Define tablas, índices, vistas</text>
  <rect x="340" y="50" width="280" height="90" rx="6" fill="#2d8659"/><text x="480" y="78" text-anchor="middle" class="t">DML — Datos</text><text x="480" y="100" text-anchor="middle" class="s">SELECT · INSERT · UPDATE · DELETE</text><text x="480" y="120" text-anchor="middle" class="s">Consulta y modifica filas</text>
  <rect x="40" y="155" width="280" height="90" rx="6" fill="#e89822"/><text x="180" y="183" text-anchor="middle" class="t">DCL — Permisos</text><text x="180" y="205" text-anchor="middle" class="s">GRANT · REVOKE</text><text x="180" y="225" text-anchor="middle" class="s">Controla privilegios</text>
  <rect x="340" y="155" width="280" height="90" rx="6" fill="#003d73"/><text x="480" y="183" text-anchor="middle" class="t">TCL — Transacciones</text><text x="480" y="205" text-anchor="middle" class="s">COMMIT · ROLLBACK · SAVEPOINT</text><text x="480" y="225" text-anchor="middle" class="s">Confirma o deshace cambios</text>
  <text x="650" y="288" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ISO9075]</text>
</svg>
```

---

## D6 · Tipos de índice

**Sección**: §2.8 — Índices
**Propósito**: Comparar B+tree, hash y bitmap según su uso ideal.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Comparación de tipos de índice: B+tree para igualdad y rango, hash solo para igualdad, bitmap para columnas de baja cardinalidad">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">¿Qué índice usar?</text>
  <rect x="30" y="48" width="200" height="120" rx="6" fill="#0055a0"/><text x="130" y="74" text-anchor="middle" class="t">B+tree (por defecto)</text><text x="130" y="98" text-anchor="middle" class="s">Igualdad = </text><text x="130" y="116" text-anchor="middle" class="s">Rango BETWEEN, &lt;, &gt;</text><text x="130" y="134" text-anchor="middle" class="s">Orden ORDER BY</text><text x="130" y="156" text-anchor="middle" class="s">Equilibrado y enlazado</text>
  <rect x="245" y="48" width="190" height="120" rx="6" fill="#2d8659"/><text x="340" y="74" text-anchor="middle" class="t">Hash</text><text x="340" y="100" text-anchor="middle" class="s">Solo igualdad exacta</text><text x="340" y="120" text-anchor="middle" class="s">Muy rápido</text><text x="340" y="142" text-anchor="middle" class="s">No sirve para rangos</text>
  <rect x="450" y="48" width="200" height="120" rx="6" fill="#e89822"/><text x="550" y="74" text-anchor="middle" class="t">Bitmap</text><text x="550" y="100" text-anchor="middle" class="s">Baja cardinalidad</text><text x="550" y="120" text-anchor="middle" class="s">(sexo, distrito)</text><text x="550" y="142" text-anchor="middle" class="s">OLAP; penaliza escrituras</text>
  <rect x="30" y="195" width="620" height="70" rx="6" fill="#fbeeed"/><text x="340" y="220" text-anchor="middle" fill="#d13c3c" font="700 12px system-ui,sans-serif">El índice acelera lecturas pero penaliza escrituras y ocupa espacio</text><text x="340" y="244" text-anchor="middle" class="l">Indexar columnas selectivas y consultadas, no todas. Índice compuesto: regla del prefijo izquierdo.</text>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: RAMAKRISHNAN, cap. 8]</text>
</svg>
```

---

## D7 · Conceptos del modelo relacional

**Sección**: §3.1 — Conceptos básicos
**Propósito**: Anclar relación/tupla/atributo/dominio/grado/cardinalidad sobre una tabla.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Sobre una tabla: la relación es la tabla, la tupla es una fila, el atributo una columna, el grado el número de columnas y la cardinalidad el número de filas">
  <style>.k{font:700 11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}.a{font:600 11px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="250" y="26" text-anchor="middle" class="h">Relación HABITANTE (grado 3, cardinalidad 3)</text>
  <rect x="120" y="44" width="260" height="26" fill="#0055a0"/><text x="150" y="62" class="k">dni</text><text x="240" y="62" class="k">nombre</text><text x="330" y="62" class="k">distrito</text>
  <rect x="120" y="70" width="260" height="24" fill="#e8f0f8"/><text x="150" y="87" class="l">0001A</text><text x="240" y="87" class="l">Ana</text><text x="335" y="87" class="l">1</text>
  <rect x="120" y="94" width="260" height="24" fill="#fff"/><text x="150" y="111" class="l">0002B</text><text x="240" y="111" class="l">Luis</text><text x="335" y="111" class="l">2</text>
  <rect x="120" y="118" width="260" height="24" fill="#e8f0f8"/><text x="150" y="135" class="l">0003C</text><text x="240" y="135" class="l">Eva</text><text x="335" y="135" class="l">1</text>
  <text x="400" y="60" class="a">← esquema / atributos (columnas)</text>
  <text x="400" y="106" class="a">← tupla (fila)</text>
  <line x1="150" y1="155" x2="150" y2="175" stroke="#d13c3c"/><line x1="370" y1="155" x2="370" y2="175" stroke="#d13c3c"/><text x="250" y="190" text-anchor="middle" class="a">grado = nº de columnas = 3</text>
  <text x="60" y="200" class="l">Atributo = columna · Dominio = valores válidos del atributo (p. ej. distrito ∈ 1..21)</text>
  <text x="60" y="222" class="l">Cardinalidad = nº de filas = 3 · No hay tuplas duplicadas (es un conjunto)</text>
  <text x="60" y="244" class="l">Orden de filas y columnas: irrelevante en el modelo teórico</text>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CODD70; DATE, cap. 6]</text>
</svg>
```

---

## D8 · Tipos de claves

**Sección**: §3.2 — Claves: candidata, primaria, alternativa, superclave y ajena
**Propósito**: Mostrar el anidamiento superclave ⊇ candidata ⊇ primaria y la clave ajena.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 620 340" role="img" aria-label="Las superclaves contienen a las claves candidatas; una de las candidatas se elige como clave primaria y las demás son alternativas; la clave ajena referencia otra tabla">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#0055a0}.s{font:11px system-ui,sans-serif;fill:#444}.b{font:600 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="230" y="26" text-anchor="middle" class="t">Jerarquía de claves</text>
  <ellipse cx="230" cy="160" rx="200" ry="120" fill="#e8f0f8" stroke="#6ea3d2"/><text x="230" y="62" text-anchor="middle" class="t">Superclaves</text>
  <ellipse cx="230" cy="175" rx="150" ry="90" fill="#cfe0f1" stroke="#3378b9"/><text x="230" y="110" text-anchor="middle" class="t">Claves candidatas (mínimas)</text>
  <ellipse cx="230" cy="195" rx="92" ry="52" fill="#0055a0"/><text x="230" y="190" text-anchor="middle" class="b">Clave primaria</text><text x="230" y="208" text-anchor="middle" class="b">(elegida, sin nulos)</text>
  <text x="230" y="148" text-anchor="middle" class="s">alternativas = candidatas no elegidas</text>
  <rect x="460" y="120" width="130" height="80" rx="6" fill="#2d8659"/><text x="525" y="150" text-anchor="middle" class="b">Clave ajena</text><text x="525" y="170" text-anchor="middle" class="b">(FK) → PK</text><text x="525" y="186" text-anchor="middle" class="b">de otra tabla</text>
  <text x="310" y="312" text-anchor="middle" class="s">superclave ⊇ candidata ⊇ primaria · la FK da integridad referencial</text>
  <text x="610" y="330" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: DATE, cap. 9]</text>
</svg>
```

---

## D9 · Operadores del álgebra relacional

**Sección**: §3.4 — Álgebra relacional
**Propósito**: Listar operadores primitivos y derivados con su símbolo y efecto.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Operadores del álgebra relacional: cinco primitivos (selección, proyección, unión, diferencia, producto cartesiano) y derivados (join, intersección, división)">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Álgebra relacional (lenguaje procedimental)</text>
  <rect x="30" y="44" width="320" height="150" rx="6" fill="#eef3f9" stroke="#0055a0"/><text x="190" y="64" text-anchor="middle" class="h">5 primitivos</text>
  <rect x="45" y="74" width="145" height="30" rx="4" fill="#0055a0"/><text x="117" y="94" text-anchor="middle" class="s">σ Selección (filas)</text>
  <rect x="195" y="74" width="145" height="30" rx="4" fill="#0055a0"/><text x="267" y="94" text-anchor="middle" class="s">π Proyección (columnas)</text>
  <rect x="45" y="110" width="145" height="30" rx="4" fill="#0055a0"/><text x="117" y="130" text-anchor="middle" class="s">∪ Unión</text>
  <rect x="195" y="110" width="145" height="30" rx="4" fill="#0055a0"/><text x="267" y="130" text-anchor="middle" class="s">− Diferencia</text>
  <rect x="45" y="146" width="295" height="30" rx="4" fill="#0055a0"/><text x="192" y="166" text-anchor="middle" class="s">× Producto cartesiano</text>
  <rect x="370" y="44" width="290" height="150" rx="6" fill="#eaf5ef" stroke="#2d8659"/><text x="515" y="64" text-anchor="middle" class="h">Derivados</text>
  <rect x="385" y="74" width="260" height="30" rx="4" fill="#2d8659"/><text x="515" y="94" text-anchor="middle" class="s">⋈ Join (natural, theta, externo)</text>
  <rect x="385" y="110" width="260" height="30" rx="4" fill="#2d8659"/><text x="515" y="130" text-anchor="middle" class="s">∩ Intersección</text>
  <rect x="385" y="146" width="260" height="30" rx="4" fill="#2d8659"/><text x="515" y="166" text-anchor="middle" class="s">÷ División («para todos»)</text>
  <text x="340" y="222" text-anchor="middle" class="l">σ filtra FILAS · π elige COLUMNAS · el resultado es siempre otra relación (se componen)</text>
  <text x="340" y="246" text-anchor="middle" class="l">Equivale en poder expresivo al cálculo relacional (declarativo)</text>
  <text x="670" y="328" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CODD70; ELMASRI, cap. 8]</text>
</svg>
```

---

## D10 · Las tres anomalías

**Sección**: §4.1 — Normalización: objetivos, redundancia y anomalías
**Propósito**: Mostrar las anomalías de inserción, borrado y actualización sobre una tabla redundante.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Las tres anomalías de un diseño no normalizado: inserción, borrado y actualización, causadas por la redundancia de datos">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <text x="330" y="26" text-anchor="middle" class="h">Redundancia → tres anomalías</text>
  <rect x="220" y="40" width="220" height="40" rx="6" fill="#d13c3c"/><text x="330" y="58" text-anchor="middle" class="t">Dato repetido en muchas filas</text><text x="330" y="73" text-anchor="middle" class="s">(p. ej. nombre_distrito en cada habitante)</text>
  <rect x="30" y="120" width="190" height="110" rx="6" fill="#0055a0"/><text x="125" y="146" text-anchor="middle" class="t">Inserción</text><text x="125" y="172" text-anchor="middle" class="s">No puedo dar de alta</text><text x="125" y="190" text-anchor="middle" class="s">un distrito sin tener</text><text x="125" y="208" text-anchor="middle" class="s">al menos un habitante</text>
  <rect x="235" y="120" width="190" height="110" rx="6" fill="#0055a0"/><text x="330" y="146" text-anchor="middle" class="t">Borrado</text><text x="330" y="172" text-anchor="middle" class="s">Borrar al último</text><text x="330" y="190" text-anchor="middle" class="s">habitante elimina el</text><text x="330" y="208" text-anchor="middle" class="s">nombre del distrito</text>
  <rect x="440" y="120" width="190" height="110" rx="6" fill="#0055a0"/><text x="535" y="146" text-anchor="middle" class="t">Actualización</text><text x="535" y="172" text-anchor="middle" class="s">Cambiar el nombre</text><text x="535" y="190" text-anchor="middle" class="s">obliga a tocar TODAS</text><text x="535" y="208" text-anchor="middle" class="s">las filas (inconsistencia)</text>
  <path d="M280 80 L150 118" stroke="#888" stroke-width="2"/><path d="M330 80 L330 118" stroke="#888" stroke-width="2"/><path d="M380 80 L520 118" stroke="#888" stroke-width="2"/>
  <text x="330" y="258" text-anchor="middle" class="l">Solución: normalizar (3FN) → cada hecho se guarda una sola vez</text>
  <text x="650" y="288" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ELMASRI, cap. 14]</text>
</svg>
```

---

## D11 · Las formas normales (anidadas)

**Sección**: §4.1-2.12 — Normalización
**Propósito**: Mostrar el anidamiento 1FN ⊃ 2FN ⊃ 3FN ⊃ BCNF ⊃ 4FN ⊃ 5FN y qué exige cada una.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 360" role="img" aria-label="Las formas normales son cada vez más estrictas y están anidadas: 1FN contiene 2FN, que contiene 3FN, BCNF, 4FN y 5FN">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:10px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="320" y="24" text-anchor="middle" class="h">Formas normales (cada una incluye la anterior)</text>
  <rect x="40" y="36" width="560" height="300" rx="8" fill="#cfe0f1"/><text x="320" y="54" text-anchor="middle" class="t" fill="#003d73">1FN — valores atómicos</text>
  <rect x="80" y="64" width="480" height="256" rx="8" fill="#9cc0e3"/><text x="320" y="82" text-anchor="middle" class="t" fill="#003d73">2FN — sin dependencias parciales</text>
  <rect x="120" y="92" width="400" height="212" rx="8" fill="#5e97ce"/><text x="320" y="110" text-anchor="middle" class="t">3FN — sin dependencias transitivas</text>
  <rect x="160" y="120" width="320" height="166" rx="8" fill="#0055a0"/><text x="320" y="138" text-anchor="middle" class="t">BCNF — todo determinante es clave</text>
  <rect x="200" y="148" width="240" height="118" rx="8" fill="#024" /><text x="320" y="166" text-anchor="middle" class="t">4FN — sin dep. multivaluadas</text>
  <rect x="240" y="176" width="160" height="70" rx="8" fill="#2d8659"/><text x="320" y="208" text-anchor="middle" class="t">5FN</text><text x="320" y="226" text-anchor="middle" class="s">sin dep. de reunión</text>
  <text x="320" y="350" text-anchor="middle" class="l">Objetivo práctico habitual: 3FN / BCNF</text>
  <text x="630" y="356" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CODD72; FAGIN77]</text>
</svg>
```

---

## D12 · Estructura de un índice B+tree

**Sección**: §2.8 — Índices
**Propósito**: Ilustrar el árbol equilibrado con hojas enlazadas (igualdad y rango).

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Estructura de un índice B+tree: un nodo raíz, nodos intermedios de guía y hojas enlazadas que contienen los punteros a las filas y permiten recorridos por rango">
  <style>.b{font:600 11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.h{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Índice B+tree (equilibrado, hojas enlazadas)</text>
  <rect x="295" y="44" width="90" height="34" rx="4" fill="#003d73"/><text x="340" y="66" text-anchor="middle" class="b">Raíz [50]</text>
  <rect x="140" y="120" width="120" height="34" rx="4" fill="#0055a0"/><text x="200" y="142" text-anchor="middle" class="b">[20 | 35]</text>
  <rect x="420" y="120" width="120" height="34" rx="4" fill="#0055a0"/><text x="480" y="142" text-anchor="middle" class="b">[70 | 90]</text>
  <path d="M320 78 L210 118" stroke="#888" stroke-width="1.5"/><path d="M360 78 L470 118" stroke="#888" stroke-width="1.5"/>
  <rect x="40" y="200" width="100" height="32" rx="4" fill="#6ea3d2"/><text x="90" y="221" text-anchor="middle" class="b">10·15·18</text>
  <rect x="150" y="200" width="100" height="32" rx="4" fill="#6ea3d2"/><text x="200" y="221" text-anchor="middle" class="b">22·30·33</text>
  <rect x="290" y="200" width="100" height="32" rx="4" fill="#6ea3d2"/><text x="340" y="221" text-anchor="middle" class="b">40·45·48</text>
  <rect x="430" y="200" width="100" height="32" rx="4" fill="#6ea3d2"/><text x="480" y="221" text-anchor="middle" class="b">55·65·68</text>
  <rect x="555" y="200" width="100" height="32" rx="4" fill="#6ea3d2"/><text x="605" y="221" text-anchor="middle" class="b">75·85·95</text>
  <path d="M170 154 L90 198" stroke="#888"/><path d="M210 154 L200 198" stroke="#888"/><path d="M230 154 L340 198" stroke="#888"/><path d="M460 154 L480 198" stroke="#888"/><path d="M500 154 L605 198" stroke="#888"/>
  <path d="M140 216 L150 216" stroke="#2d8659" stroke-width="2"/><path d="M250 216 L290 216" stroke="#2d8659" stroke-width="2"/><path d="M390 216 L430 216" stroke="#2d8659" stroke-width="2"/><path d="M530 216 L555 216" stroke="#2d8659" stroke-width="2"/>
  <text x="340" y="266" text-anchor="middle" class="l">Hojas al mismo nivel + enlazadas (verde): igualdad (=) y rango (BETWEEN, &lt;, &gt;) eficientes</text>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: RAMAKRISHNAN, cap. 10]</text>
</svg>
```
