# Redbee Academy - Ejercicios SQL


## Comenzar


### Iniciar base de datos

```sh
docker-compose up -d
```


### Detener base de datos

```sh
docker-compose stop
```


### Eliminar base de datos

```sh
docker-compose down
```


## Ejercicios


### Ejercicio 1

Listar el nombre y el precio unitario de todos los productos.


### Ejercicio 2

Listar el ID y el nombre de todos los productos que no hayan sido descontinuados.


### Ejercicio 3

Listar el ID, el nombre, la dirección y la ciudad de todos los clientes que sean argentinos.


### Ejercicio 4

¿Cuál es el ID y el nombre del producto más barato de la lista? ¿Cuál es el más caro?


### Ejercicio 5

Listar el ID, el nombre, la cantidad por unidad y las unidades en stock de todos los productos que no hayan sido descontinuados y de los cuales haya al menos 100 unidades en stock.


### Ejercicio 6

Listar el ID, el nombre, el precio unitario y las unidades en stock de todos los productos que entrega el proveedor 25.


### Ejercicio 7

Listar el ID, el nombre, la cantidad por unidad, el precio unitario, las unidades en stock de los productos que no hayan sido descontinuados, que tengan menos de 10 unidades en stock y que sean provistos por empresas en Estados Unidos o en el Reino Unido. Adicionalmente, por cada uno incluir el nombre del proveedor, el nombre del contacto, la ciudad y el país en los que se encuentra y el número de teléfono.


### Ejercicio 8

Combinar en una única lista las 10 últimas órdenes enviadas (ordenadas por la fecha de envío, y el ID de la orden si fuera necesario) y las 10 últimas órdenes que aún no hayan sido enviadas (ordenadas por la fecha de la orden, y el ID de la orden si fuera necesario).


### Ejercicio 9

Listar los nombres de los barcos mexicanos (sin repetirlos) que hayan despachado órdenes en el año 1996.


### Ejercicio 10

Listar los nombres y las cargas totales de los 5 barcos que más carga transportaron en los últimos 6 meses del año 1997.


### Ejercicio 11

¿Cuáles fueron, en cantidad de unidades, los tres productos menos vendidos de enero de 1998? Indicar el ID y el nombre de cada producto y las cantidades correspondientes.


### Ejercicio 12

Listar el ID, el nombre y la descripción de las 4ta., 5ta. y 6ta. categorías de producto más vendidas (considerando el monto total) del año 1996.


### Ejercicio 13

Considerando sólo los meses de julio de 1996, agosto de 1997 y marzo de 1998, ¿quién fue el empleado (ID, apellido, nombre y fecha de contratación) que más productos de proveedores situados en Escandinavia (Noruega, Suecia, Dinamarca y Finlandia) vendió (considerando el monto total).


### Ejercicio 14

Listar el ID, el apellido y el nombre de los empleados que no realizaron ninguna venta en febrero de 1997.


### Ejercicio 15

Agregar a los siguientes transportistas a la base de datos:

| shipper_id | company_name     | phone           |
|------------|------------------|-----------------|
| 7          | Maersk           | +45 70716341    |
| 8          | Hapag-Lloyd AG   | +1 732-562-1800 |
| 9          | Evergreen Marine | 886-02-25057766 |


### Ejercicio 16

Actualizar la página (homepage) de todos los proveedores que no la tengan definida a valores que sigan el formato:

```
https://www.google.com/search?q={{nombre_proveedor}}
```

Para sanitizar el nombre del proveedor `nombre_proveedor` se deberá tener en cuenta lo siguiente:

- Los espacios en blanco deben ser reemplazados por el signo más (`+`).
- Los caracteres de comilla simple (`'`) y de ampersand (`&`) deben ser eliminados.

Por ejemplo,

| supplier_id | company_name                | homepage                                                   |
|-------------|-----------------------------|------------------------------------------------------------|
| 1           | Exotic Liquids              | https://www.google.com/search?q=Exotic+Liquids             |
| 11          | Heli Süßwaren GmbH & Co. KG | https://www.google.com/search?q=Heli+Süßwaren+GmbH++Co.+KG |
| 21          | Lyngbysild                  | https://www.google.com/search?q=Lyngbysild                 |

CONSEJO: La función `translate` de Postgres puede utilizarse para realizar la sanitización.
