-- 1 Listar el nombre y el precio unitario de todos los productos.
select product_name, unit_price
from product p;

-- 2 Listar el ID y el nombre de todos los productos que no hayan sido descontinuados.
select product_id, product_name
from product p
where discontinued != 1;

-- 3 Listar el ID, el nombre, la dirección y la ciudad de todos los clientes que sean argentinos.
select customer_id, contact_name, address, city
from customer c 
where c.country  = 'Argentina';

-- 4 ¿Cuál es el ID y el nombre del producto más barato de la lista? 
select product_id, product_name
from product p 
order by unit_price asc limit 1;

-- Another solution
select product_id, product_name, unit_price 
from product  
where unit_price = (select MIN(unit_price) from product);

-- ¿Cuál es el más caro?
select product_id, product_name
from product p 
order by unit_price desc limit 1;

/* 5 Listar el ID, el nombre, la cantidad por unidad y las unidades en stock de 
todos los productos que no hayan sido descontinuados y de los cuales haya al menos 100 unidades en stock. */
select product_id, product_name, quantity_per_unit, units_in_stock
from product p
where p.discontinued = 0 and p.units_in_stock > 99;

/* 6 Listar el ID, el nombre, el precio unitario y las unidades en stock de todos los
 productos que entrega el proveedor 25. */
select product_id, product_name, unit_price, units_in_stock, p.supplier_id 
from product p
left join supplier s
on p.supplier_id = s.supplier_id
where s.supplier_id = 25;

/* 7 Listar el ID, el nombre, la cantidad por unidad, el precio unitario, las unidades en stock 
   de los productos que no hayan sido descontinuados, que tengan menos de 10 unidades en stock y 
 que sean provistos por empresas en Estados Unidos o en el Reino Unido. 
 Adicionalmente, por cada uno incluir el nombre del proveedor, el nombre del contacto, la ciudad 
 y el país en los que se encuentra y el número de teléfono. */

select p.product_id, p.quantity_per_unit, p.unit_price, p.units_in_stock, s.company_name,
		s.contact_name, s.city, s.country, s.phone
from product p
join supplier s 
on p.supplier_id = s.supplier_id
where p.discontinued = 0 and p.units_in_stock < 10 and s.country in ('USA', 'UK');

-- Another option
select product_id , product_name, units_in_stock, company_name, contact_name, city, country, phone   from product p
right join (select supplier_id, company_name, contact_name, city, country, phone from supplier s 
where country = 'USA' 
or country = 'UK') t1
on p.supplier_id = t1.supplier_id 
where discontinued = 0
and units_in_stock < 10

/* 8 Combinar en una única lista las 10 últimas órdenes enviadas (ordenadas por la fecha de envío, 
 y el ID de la orden si fuera necesario) y las 10 últimas órdenes que aún no hayan sido enviadas 
 (ordenadas por la fecha de la orden, y el ID de la orden si fuera necesario). */
(

(select *
from "order" o 
where o.shipped_date is not null
order by order_date, order_id desc limit 10)

union 

(select *
from "order" o2 
where o2.shipped_date is null 
order by o2.order_date, o2.order_id desc limit 10)

) 

order by shipped_date;

/* 9 Listar los nombres de los barcos mexicanos (sin repetirlos) que hayan despachado órdenes
   en el año 1996. */
select o.ship_name 
from "order" o 
where o.ship_country = 'Mexico' and o.shipped_date between '1996-01-01' and '1996-12-31'
group by o.ship_name;

/* 10 Listar los nombres y las cargas totales de los 5 barcos que más carga transportaron
en los últimos 6 meses del año 1997.*/
select o.ship_name, sum(od.quantity) as total_loads
from "order" o 
join order_detail od 
on o.order_id = od.order_id 
where shipped_date between '1997-07-01' and '1997-12-31'
group by ship_name 
order by total_loads desc limit 5;

/* 11 ¿Cuáles fueron, en cantidad de unidades, los tres productos menos vendidos de enero de 1998?
Indicar el ID y el nombre de cada producto y las cantidades correspondientes. */
select p.product_id, p.product_name
from "order" o 
join order_detail od on o.order_id = od.order_id 
join product p on od.product_id = p.product_id 
where o.shipped_date between '1998-01-01' and '1998-01-31'
group by p.product_id, p.product_name
order by sum(od.quantity) asc limit 3;

/* 12 Listar el ID, el nombre y la descripción de las 4ta., 5ta. y 6ta. categorías de producto 
   más vendidas (considerando el monto total) del año 1996.*/
select category_id, category_name, description from(
select c.category_id, c.category_name, c.description, sum(od.unit_price * od.quantity) as total
from category c
join product p on c.category_id = p.category_id 
join order_detail od on p.product_id = od.product_id 
join "order" o on od.order_id = o.order_id 
where o.shipped_date between '1996-01-01' and '1996-12-31'
group by c.category_id
order by total desc
limit 3 offset 3) as foo;
