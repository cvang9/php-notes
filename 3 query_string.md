###                             Q U E R Y  S T R I N G   U S I N G    PHP

`How can we get a query string that we passed in url ? `
`Ans. Answer is hidden in the question ` {{ $_GET }}

By using {{ $_GET[] }} method we can simply get the query params that we had provided in URL;
The $_GET array contains an array of key value pairs from the query string

ex: `localhost/php/a.php?id=21`
{{
    <?php  echo $_GET['id'];  ?>  // 21
}}



# SQL INJECTION 
in the address bar a user can type anything even a sql statement. and suppose we are using that id like:
{{ SELECT * FROM table WHERE id=$_GET['id'] }}, in place of id user can send a malicious SQL query also.

" To overcome the issue we use validators "
ex:  is_numeric( $data ) will return true if data is a numeric value else returns false;

