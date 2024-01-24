###                             IMPORTING ANOTHER PHP FILE

We are having different ways to import a php file each of one having different functionality.

# 1. include 
Using include, php import all the php code from the provided path and if any error occurs then it shows the warning and continue the execution.
ex: `<?php include 'header.php' ?>`

# 2. require
On the other hand require also does same thing but if in this case an error occurs then the execution will stop.
ex: `<?php require 'header.php' ?>`


# 3 and 4. include_once and require_once
Does work the same but along with it also keep track if the file is already imported or not, if it is imported then it will not import again and that's why it is slight slow.