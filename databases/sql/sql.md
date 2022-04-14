# SQL

w3schools for more information about SQL

**Keywords**:

* Create
* Read
* Update
* Destroy&#x20;

"CRUD"

**Creating a table:**\
****

```sql
# Table with more options, such as auto increment ID
CREATE TABLE logins (
    id INT NOT NULL AUTO_INCREMENT,
    username VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    date_of_joining DATETIME DEFAULT NOW(),
    PRIMARY KEY (id)
    );
```



```
CREATE TABLE products (
  id INT NOT NULL, 
  name STRING,
  price MONEY,
  PRIMARY KEY (id)
  )
```

id INT NOT NULL sets ID type as int and makes sure that this field cannot be empty.\
PRIMARY KEY sets the primary key for table. \
Other fields are just columns.

**Showing the table:**

```
SELECT * FROM products 
```

"Show ALL from table products"

**Inserting data into table**

```
# Inserting one value only
INSERT INTO products
VALUES (1, "Pen", 1.20)
```

**Inserting data to specific fields only, ex if you dont have data for certain columns**

```shell-session
# Inserting values with multiple records at once
INSERT INTO logins(username, password) 
VALUES ('john', 'john123!'), 
('tom', 'tom123!');
```

```
INSERT INTO products (id, name)
VALUES (2, "Pencil")
```



**Reading data** SQL SELECT

Select all

```
SELECT * FROM "products";
```

Select specific column

```
SELECT name, price FROM "products"; 
```

Select specific row

```
SELECT * FROM products WHERE id=1
```

**Update data** Update one piece of data, eg price of pencil

```
UPDATE products
SET price = 0.80
WHERE id=2
```

Adding a column (Will be added with NULL value)

```
ALTER TABLE products
ADD stock INT
```

**Deleting data**

```
DELETE FROM products
WHERE id = 2
```

**SQL Foreign Key**

```
CREATE TABLE orders (
id INT NOT NULL,
order_number INT,
product_id INT, 
PRIMARY KEY (id),
FOREIGN KEY (customer_id) REFERENCES customers(id),
FOREIGN KEY (product_id) REFERENCES products(id)
)
```

**Creating order**

```
INSERT INTO orders
VALUES (1, 4362, 2, 1)
```

**Joining tables** Joins tables where we specify which columns you want. This will create a table with order\_number, customer name, lastname and address.

```
SELECT orders.order_number, customers.first_name, customers.last_name, customer.address
FROM orders 
INNER JOIN customers ON orders.customer_id = customers.id
```
