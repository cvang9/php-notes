###                                   Return Statement While importing

`While we import any file using require/include, along with we also can expect a return value from file`


{{
    // classes/db.php
    $db = new Database();                                                                                          $
    return $db->connect_db();


    // *root-directory
    $conn = require 'classes/db.php';

}}
