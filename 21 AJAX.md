###                             ASYNCRONOUS JAVASCRIPT AND XML 

`Usually when we send a request to the server, it responses to the client with a complete html page due to which browser has to re-render the entire page completely with a reload`

Introducing AJAX:
AJAX allows us to update the html content without reloading but the info. which is going to be updated it must be small. 
It also involves communication with server  but in a different way that returns only the required data instead of returning the whole page.


# Multiplexing php with ajax using jquery

{{
    
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>

       <div>
         <h1 id="time" > The time is : <?= date('g:i:s'); ?> </h1>
         <button id="btn" > Refresh </button>
       </div>
        
        // jQuery
        <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>

        // Local script
        <script>
           $("#id").on( 'click', function(){

              $.ajax('filename.php')         
               .done( function(data){              

                // done method is called when filename is executed.
                // data is the data which is returned by the file
                     $("#time").html(data);                                                      $
                    // html() method is used to exchange the content of any element
                      
               })
           });

        </script>
    </body>
    </html>

}}

% Filename.php

{{
    <?= date("g:i:s"); ?>
}}