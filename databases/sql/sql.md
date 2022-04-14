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

**Sorting**

```sql
# Sort by password in ascending order 
SELECT * FROM logins ORDER BY password;

# Sort by descending order
SELECT * FROM logins ORDER BY password DESC;

# Sort by multiple columns
SELECT * FROM logins ORDER BY password DESC, id ASC;

## Limiting Results ##
# Limits the amount of record to 2 
SELECT * FROM logins LIMIT 2;

# Limits with an offset
SELECT * FROM logins LIMIT 1, 2;

## Using Where ## 
Syntax:
SELECT * FROM table_name WHERE <condition>;

# Show data where id is greather than 1
SELECT * FROM logins WHERE id > 1;

# Searching for users with admin username 
SELECT * FROM logins where username = 'admin';

## Sorting using LIKE ##
# Takes all records where username STARTS with admin
SELECT * FROM logins WHERE username LIKE 'admin%';
# % is a wildcard and matches all characters after admin

# Searches for users with 5 characters in username
SELECT * FROM logins WHERE username like '_____';

# Search example using Operators
SELECT * FROM logins WHERE username != 'john' AND id > 1;

```

**Update data** \
Update one piece of data, eg price of pencil

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

**Joining tables** \
Joins tables where we specify which columns you want. This will create a table with order\_number, customer name, lastname and address.

```
SELECT orders.order_number, customers.first_name, customers.last_name, customer.address
FROM orders 
INNER JOIN customers ON orders.customer_id = customers.id
```

**Dropping tables**\
****To be used with caution as table will be permanently be deleted with no confirmation.&#x20;

```shell-session
DROP TABLE logins;
```

**Alter tables**\
****Alters information in table

```sql
# Adds a column to the logins table
ALTER TABLE logins ADD newColumn INT;

# Renames column 
ALTER TABLE logins RENAME COLUMN newColumn TO oldColumn;

# Alters data type for a column
ALTER TABLE logins MODIFY oldColumn DATE;

# Drops a column in a table
ALTER TABLE logins DROP oldColumn;
```

**Update statement**

Alter changes a tables properties, update updates specific records within a table, based on certain conditions.\
&#x20;\
Syntax:&#x20;

```sql
# With update you have to specify WHERE
UPDATE table_name SET column1=newvalue1, column2=newvalue2, ... WHERE <condition>;

# Updates password to change_password where ID number is greather than 1
UPDATE logins SET password = 'change_password' WHERE id > 1;
```

**Operators**\
****Logical operators for using multiple conditions at once.&#x20;

**AND operator**\
****Takes a condition and returns True or False

```sql
# Example, will return True
# Instead of AND you can also use &&
SELECT 1 = 1 AND 'test' = 'test';

# Example, will return False
SELECT 1 = 1 AND 'test' = 'sdgfg';
```

**OR operator**\
****Takes 2 statements and evaluates if either one of them is True

```sql
# Example, will return True
# Instead of OR you can also use ||
SELECT 1 = 1 OR 'abc' = 'cba';

# Example will return False
SELECT 1 = 2 OR 'abc' = 'cba';
```

**NOT operator**\
****Statement will be converted from True to False, or False to True etc

```sql
# Example, returns False
# Instead of NOT you can put an ! before the =. 
SELECT NOT 1 = 1;

# Example, return True
SELECT NOT 1 = 2;
```

**Multiple Operators Precedence**\
****SQL also supports various other operations.&#x20;

```
Division (/), Multiplication (*), and Modulus (%)
Addition (+) and subtraction (-)
Comparison (=, >, <, <=, >=, !=, LIKE)
```

&#x20;**** \
****
