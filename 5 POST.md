###                             A C C E P T    P O S T    R E Q U E S T     D A T A

` When we send a post request with some data we can access it using`{{  $_POST }} variable, likewise $_GET it is also an associative array that contains data.
Its index is what we pass in `name` attribute of input element.

ex:

{{
    <?php

    // REMARK FUNCTION
    if( $_SERVER["REQUEST_METHOD"] == "POST" )
    {
        var_dump($_POST["name"]);
    }

    ?>

    <?php include 'includes/header.php' ?>

    <div>
        <form method="post">
            <label for="name" > Name </label>
            <input type="text" id="name" name="name" />

            <button type="submit">Submit</button>
        </form>
    </div>

    <?php include 'includes/footer.php' ?>
}}