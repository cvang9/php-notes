###                             Q U E R Y    U S I N G     M Y S Q L

`Once the connection is established we can successfuly create query using a func mysqli_query( param1, param2)`

<huehuehue- mysqli_query( $con, $sql ); > 
It will take two parameters:
`1. The connection instance
`2. The sql query in double_quotes


{{
    // STEP 1: CREATE A SQL QUERY
    $sql="SELECT * FROM persons";

    % STEP 2: GENERATE QUERY INSTANCE
    % function will return false if it face any kind of error, returns array on SELECT, SHOW, DESC, EXPLAIN and returns true on rest successfull queries;
    $query = mysqli_query( $con, $sql );

    // STEP 3: GET THE ORIGINAL DATA
    if( $query === false ){           
        echo 'error';
    } 
    else {
        //  mysqli_fetch_all will fetch out all the table data in form of 2D Matrix or Associative array.
        $data = mysqli_fetch_all($query);
    }
}}


<huehuehue- What if anyone need one single row >
For this we have an another function: {{ mysqli_fetch_assoc() }} 
<!-- If we use this function then we get a simple array with indexes as a column name -->




# INSERT QUERY USING PHP AND GET CORRESPONDING ID

{{

    $sql = "INSERT INTO..." ;

    $result = mysqli_query( $conn, $sql );

    if( $result === false ){
        echo 'query_unsuccessfull';
    }
    else{

        // the below function will return the auto generated id of latest executed query.
        $id = mysqli_insert_id($conn);
        echo $id;
    }
}}



# We stuck in a situation:- in any input if we need to insert a quoted text then it will breaks.

the solution for one of these is using a backslash '\' as a escape character sequence.
we have a function that does exactly the same thing for us 

# mysqli_escape_string( $conn, '_VALUE_' )

We can perform query like:

$sql = "INSER INTO table (title) VALUES ( mysqli_escape_string( ' o'clock ' ) )";

