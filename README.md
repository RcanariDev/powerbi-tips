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




