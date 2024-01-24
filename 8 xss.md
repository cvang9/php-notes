###                            AVOID  CROSS  SITE  SCRIPTING  USING   PHP

It is the type of attack where user enter some javascript tags in place of some input tags or textarea.
for ex: 
in an textarea enter ->   <?php echo $password; ?> 
This may display the value of $password variable.


$ The problem can be solved using a function `htmlspecialchars($_POST['message'])`                                 $
what the function do is convert the special character into html entities. like   "<" will encoded as  "&lt" in form of html entity. This will make sure no html will be compiled inside and user will also get thier exact written code.