###                          FILTER_VAR FUNCTION IN   PHP

`for some specific input if we want to validate that like checking if it is a integer having min value a, similarly having max value b if it is not then return default value $`

{{

$value = filter_var( $inp , FILTER_VALIDATE_INT );    
// convert any integer_string to integer 
// returns false if input is not a integer_string

// what if we dont want to return false instead return a default value? for that we have an optional third argument there we can simply specify that

$value = filter_var( $inp, FILTER_VALIDATE_INT, [
    'options' => [
        'default' => 1,
        'min_range' => 1, 
        'max_range' => 2  
      ]
]);

// in this case if any of cond will fail then the default value will be returned.
}}