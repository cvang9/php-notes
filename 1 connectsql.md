###                              C O N N E C T    T O     M Y S Q L

# STEP 1:
` collect all the data needed to connect with mySQL`

$db_host = "localhost";
$db_user = "sqluser";
$db_pass = "password";
$db_name = "db_name";

# STEP 2:
` use a function and pass above parameters, store its instance in a variable`
 {{ $con = mysqli_connect( $db_host, $db_user, $db_pass, $db_name ) }}

# STEP 3
` check if db is connected or not?`
{{ 
        // mysqli_connect_error() will return null if will connection established successfully
        if( mysqli_connect_error() )       
        {
            echo mysqli_connect_error();     
        }
}}



