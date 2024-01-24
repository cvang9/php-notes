###                                   AUTO IMPORTING A CLASS

we use a function called: `spl_autoload_register`:
It takes a callback in its argument and callback accepts another argument containing the name of the class which is not imported;
ex:
{{

    spl_autoload_register( function( $class) ){
        require dirname(__DIR__) 'classes/{$class}.php'; 
    }
    // __DIR__ is a constant that returns full current directory
    // dirname() returns the root directory     

 
    $db = new Database();                                                                                                            $
    // We had'nt included this db file, so php compiler before throwing error first go to above function   

}}

// To achieve this you must follow a convention.
1. The class name must start with capital letter
2. The filename consisting class must start with capital letter
3. Both classname and filename must be exactly same