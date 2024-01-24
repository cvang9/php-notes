###                                     PASSWORD HASHING IN  PHP

We have a database to store user details but storing thier password directly can be a dangerous activity.
therefore we need to store some kind of hash in our database;

PHP provides us lots of algorithms to create simple hashes. But none of them is recommended to use for passwords because thier might be a possibility to de-hash the passwords.

But we have a one function that solves the problem, it will generate multiple hashes of same input. proccess called salt hashing

{{

    $password = "$huehuehue";
    
    //create hash 
    $hashed_password = password_hash($password, PASSWORD_DEFAULT);

    // compare both password using
    $isAuthenticated = password_verify( $password, $hashed_password );

}}