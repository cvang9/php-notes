###                             PHP DATA OBJECTS

Php provides us a lot of advantage if we use object oriented functions over procedural functions.
like we can use another PDA approach to connect with the database over mysqli, but why should we use it if we are grinding well with mysqli? just because PDA allows to deal with multiple databases rather than sticking with mysql only.
For an example in future if we need to change database then the code will be same for that also.


# Connect to database via PDO:
{{

    class Database
    {

        function connect_db(){

            $db_host = "localhost";
            $db_user = "sqluser";
            $db_pass = "password";
            $db_name = "cms";

            $dsn = "mysql:host=" . $db_host . ";dbname=" . $db_name . ";charset=utf8";

            return new PDO( $dsn, $db_user, $db_pass );
        }
    }
}}


`handle error using try and catch`
{{

    try{
            $db = new PDO( $dsn, $db_user, $db_pass );

            // Set the exception attribuites 
            $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );

            return $db;

    } catch( PDOException $e ) {
            echo $e->getMessage();
    }

}}






` Metaphor from mysqli with PDOs`

<STEP1- import file and initialise class object
{{
    $db = new Database();
    $conn = $db->connect_db();
}}


<STEP2- replacing mysqli_query() fxn 
{{
    $sql = "";
    $result = $conn->query($sql) 
}}

<STEP3- replacing mysqli_error() fxn
{{
   // $result will contain false if it any error occurs
   if( $result === false )
   {
        var_dump($conn->errorInfo()); // return whole array of errors
   }
}}


<STEP3- replacing mysqli_fetch_all() fxn
{{
    if( $result === false )
   {
        var_dump($conn->errorInfo()); // return whole array of errors
   } else {
        $data = $result->fetchAll();                     // return output in the form of 2D matrix
        $data = $result->fetchAll(POD::FETCH_ASSOC);    // return output in the form of an Associative array
   }
}}






` Metaphor from prepare statements with PDOs`

<first- mysqli_prepare()
{ 
    $db = new Database();                                                                                        
    $conn = $db->connect_db();               
    <!-- replace placeholder with name i.e. :id -->
    $sql = "SELECT * FROM table WHERE id = :id";                                                                   
    
    <!-- replace mysqli_prepare with prepare() method of $conn -->
    $stmt = $conn->prepare($sql);         
                                  
    <!-- Bind values  -->
    $stmt->bindValue( ':id', $id, POD::PARAM_INT );


    <!-- execute  and fetch -->
    if( $stmt->execute() ){
  
        <!-- if we want data -->
        $data = $stmt->fetch(POD::FETCH_ASSOC);         // returns the array as index named same as the column name;


        <!-- if we want last inserted id -->
        $id = $conn->lastInsertId();
        
    }




}









