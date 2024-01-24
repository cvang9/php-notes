###                             MAKING SQL INJECTION IMPOSSIBLE

By using `mysqli_prepare()` procedure then user can never inject SQL in our data.

Procedure:

# STEP 1: ADD placeholders('?') instead of data 
$sql = "INSERT INTO table(title, content ) VALUES ( ?, ? )";                                                       $

# STEP 2: use mysqli_prepare()
$stmt = mysqli_prepare( conn, sql );                                                                               $

# STEP 3: Binding data with placeholders and execute query
if( $stmt !== false )
{
    mysqli_stmt_bind_param( $stmt, "ss", $title, $content );

   if ( mysqli_stmt_execute(#stmt) )  // function returns true   
   {
       echo 'successfuly executes';
   }
   else {                              
    echo mysqli_stmt_error($stmt);
   }
}

` Destructuring mysqli_stmt_bind_param( stmt instance, value pattern, values )`
value pattern means-> for string, use "s" 
                     for integer, use "i"
                      for double, use "d"

`since there are two strings therefore we used `ss` ;`