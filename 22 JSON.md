###                                   JSON in PHP

`convert an associative array to JSON string`
{{

    $data = [
        'one' => 1,
        'two' => 2,
        'three' => 3
    ];

    $json = json_encode($data);
}}




`convert JSON data to an associative array`
{{

    $json = '{
        "one" : 1,
        "two" : 2,
        "three" : 3
    }'

    $data = json_decode($json);
}}