# Tips para power bi

<br />


## 1. Poner un formato de fecha

Siempre se debe crear una nueva columna de fecha en Power BI, para obtener el formato de fecha que usualmente queremos ("dd/mm/yyyy").-
NO UTILIZAR directamente la fecha de la data.

Ir a "Vista de tabla" para crear la columna.

<br />

- Columna simple

```
FormatoFecha = FORMAT(DashClientesUnionTab12[Fecha],"dd/mm/yyyy")
```

- Columna más elaborada

Se utiliza **&** para concatenar valores

```
FormatoFecha1 = FORMAT(DashClientesUnionTab12[Fecha],"dd/mm/yyyy") & " (" & FORMAT(DashClientesUnionTab12[Fecha], "dddd") & ")"
```


<br />
<br />

## 2. Poner el porcentaje al costado del valor

<br />

De la data que se tiene:

- Se tiene que crear una nueva columna (para poner el porcentaje que se quiere)

```
PorClientesNuevos = IF(DashClientesUnionTab12[ClientesDistintos] = 0, 0, DashClientesUnionTab12[TotalClientesNuevos]/DashClientesUnionTab12[ClientesDistintos])
```

- Se debe crear una nueva columna, pero concatenando el valor actual con la columna porcentaje creado arriba

```
PorClientesNuevosTag = DashClientesUnionTab12[TotalClientesNuevos] & " (" & FORMAT(DashClientesUnionTab12[PorClientesNuevos], "#%") & ")"
```

- Hacemos clic al gráfico de linea que se tiene
- "Dar formato a su objeto visual"
  - "Etiqueta de datos"
    - Seleccionar la serie que queremos cambiar
    - "Valores"
        - Activar la "Etiqueta personalizada"
        - Poner la columna creada con el valor y el porcentaje (En este caso, se llama: PorClientesNuevosTag)


<p align="center">
  <img src="/img/lab11.jpg" width=30% height=30%>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="/img/lab12.jpg" width=30% height=30%>
</p>


<br />
<br />

## 3. Automatizar la medida cuando se aplica un filtro

<br />

- Se utiliza **CALCULATE()** y **ALLSELECTED()**

<br />

```
Trx Proporción = 
DIVIDE(
    SUM(Data12[Trx]),
    CALCULATE(SUM(Data12[Trx]), ALLSELECTED(Data12))
)*100
```










