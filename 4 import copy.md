###                                   AUTO IMPORTING A CLASS

`usually we code include statement to import the php files, however we can make this happen automatically using some lines of code and it works for all imports.`

{{
    // usual
    require 'includes/abc.php';
    require 'includes/def.php';
    require 'includes/fgh.php';
    require 'includes/ert.php';
}}

`instead we can use a function: ` spl_autoload_register()
<dsf- In argument it accepts a function which executes whenever php compiler did'nt get any class file and it has been used in our program. The callback itself accepts a variable which contains the name of that variable.

{{
    spl_autoload_register( function($classname){
        require "classes/{$classname.php}"; 
    });


    $db = new Database(); 
    //compiler did'nt find any specific file related to database, so before throwing error it first go to above fxn 
}}