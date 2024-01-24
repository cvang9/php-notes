###                             COOKIES   IN   PHP

Lets have a quick intro about cookie, Cookies are storage in web browser that stores small values.
In `php` we can create cookies using `setcookie( 'key', 'value' );` and get access it using`$_COOKIE['key'];`
By default cookie expire at the end of session i.e. when the browser is closed.
To add expiry of a cookie we can set it at the end parameter of `setcookie( 'key', 'value', time() + secs )`
ex: Cookie must expire after 30 days:

# setcookie( 'key', 'value', time() * 60 * 60 * 24 * 30 );



# Cookie can store just string values in its storage.