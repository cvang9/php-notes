###                             SESSIONS   IN   PHP

User sent a request to server and server give response to it. again same happens. Run the same scenerio as many times as you want but server will never know that the same person is requesting me again and again. because server is stateless.  It does'nt carry states.

So how server can identify that this is the user who had logged in and this is the user who has not logged in?
Using a token. 
At very first user sent an req. to server now server includes a token along with its response. Now everytime when same user try to request then, the request goes along with that token and using that token server identifies whether the user is authenticated or not?


<huehue- In php `sessions` allows us to use the above appproach for authentication and authorisation.


Session works in such a way, when user get reponse from the server for the first time then the token which user will got along with response is now stored in the cookies of the web browser and from now when user send its next request to server, in the request header the token is attached from that cookie which contains token id.

REMARK: Also we can create our own variables using sessions which will work same as cookie.


{{
    // Starts the session if has not created yet else resume it
    session_start();

    // We can store our data and accessed using a key
    $_SESSION['key'] = value;                                                                                                $

    % Destroy session
    session_destroy();
}}

To destroy the session we have a function named `session_destroy()`: This function destroys the all the data resisding on current session which was created during its operations. 


# However it just destroy the current session not the complete data lie in itself. 
To destroy the complete data:

{{
    session_start();

    // Unset all of the session variables.
    $_SESSION = array();                                                                                                     $

    // If it's desired to kill the session, also delete the session cookie.
    // Note: This will destroy the session, and not just the session data!
    if (ini_get("session.use_cookies")) {
        $params = session_get_cookie_params();
        setcookie(session_name(), '', time() - 42000,
            $params["path"], $params["domain"],
            $params["secure"], $params["httponly"]
        );
    }

    // Finally, destroy the session.
    session_destroy();
}}


# SESSION FIXATION ATTACK :
Our site can be vulnerable to session fixation attack where attacker can steals our session id by applying xss attack.
To prevent this at the runtime we can regenerate our session id using a fxn `session_regenerate_id(true);` 
It deletes the previous session id and generate new one while preserving the data safe; 

Add this at the time of loging in of user.

{{
        if( $username == "dogesh" && $password == "huehuehue" ){
        $_SESSION['isLoggedin'] = true;
        session_regenerate_id(true);
        header("Location:index.php");
        } else {
            $_SESSION['isLoggedin'] = false;
            $error[] = "Invalid user credentials";                                                                        $
        }    
}}



# REMARK: SESSION CAN STORE ANY TYPE OF DATA IN ITS STORAGE BUT IT IS RECOMMENDED TO STORE SIMPLE ONE ONLY.