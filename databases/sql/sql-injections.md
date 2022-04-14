# SQL Injections

Web applicatons mostly use backend databases to store data they process. To interact, we use SQL language.

Important vulnerability as databases can contain user credentials, data, creditcard numbers, etc.

**To carry out an attack you need to know**

* SQL statements syntax
* How to perform a query
* How to union the results of two queries
* How comments work

**SQL Statement example:** SELECT name, description FROM product WHERE id=9; _Asks for name and decription of a record in products table_

http://www.w3schools.com/sql/sql\_intro.asp

"#" This is a comment "--" This is another comment

* Connect to database
* Submit the query to database
* Retrieve the results

user-supplied inputs to build a query is dangerous. Users an exploit the query construction to take control over DB interaction.

To exploit Need to find where injection point is, craft payload and take control over a dynamic query To ID an injection ppoint, need to test every supplied user input used by the web application. User inputs are:

* GET parameters
* POST parameters
* HTTP Headers
  * User-Agent
  * Cookies
  * Accept Every input must be tested to conduct a professional pentest

Testing means trying to inject....

* String terminators: ' and "
* SQL Commands: SELECT, UNION, and others
* SQL Comments: # or --

Test only one injection at a time to understand what is working. Test also multiple vulnerabilities, not just one After manually finding an exploit, efficiently automate the exploitation using automatic tools.

Don't comment just two dashes, use 3 dashes because most browsers automatically remove trailing spaces in the url.

Need to know how many fields are vulnerable to exploit, do this by trial and error.

When attacking SQL vuln, keep in mind not only SELECT type queries are vulnerable. Ask yourself, is what Im doing just displaying data or modifying it?

SQLMAP most common tool **SQLMap** Detect and exploit SQL injections Test injection by hand first, and then move to tool. Be careful as SQLmap can crash the remote service. Syntax: sqlmap -u URL -p INJECTIONPARAM options

**Resources** Rooms to practice: [TryHackMe | SQL Injection](https://tryhackme.com/room/sqlinjectionlm) [TryHackMe | SQLMAP](https://tryhackme.com/room/sqlmap) [TryHackMe | Avengers Blog](https://tryhackme.com/room/avengers) [TryHackMe | OWASP Juice Shop](https://tryhackme.com/room/owaspjuiceshop) [TryHackMe | Game Zone](https://tryhackme.com/room/gamezone) [Hack The Box :: Hack The Box :: GoodGames](https://app.hackthebox.com/machines/GoodGames) [Hack The Box :: Hack The Box :: Validation](https://app.hackthebox.com/machines/Validation) [SQL Injection Fundamentals (hackthebox.com)](https://academy.hackthebox.com/module/details/33)
