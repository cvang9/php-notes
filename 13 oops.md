###                             OOP   IN   PHP

so far Object oriented programming apprach can be used in php and even php is grinding just because of the OOPs.
so its become important for us to learn PHP OOP.

STEP 1: CREATING A CLASS

{{

    <?php 

        class Item 
        {
            // properties
            ...
            // behaviour
            ...
        }
     ?>

}}

STEP 2: Creating instance(object) of a class.

{{

    class Item 
    {
      ...
    }

    $obj1 = new Item();
    $obj2 = new Item();

}}


-> The Default value of each attribute of a class is NULL untill we provide it a new value;
-> We can access the value of a property using slim-arrow: `->`
ex: 
{
{
    <?php 

    class car{
        $color;
        $topSpeed;
        $brand = 'Maruti';
    }

    $obj1 = new car();
    $obj2 = new car();

    $obj1->color = 'metallic grey';
    $obj1->topSpeed = 180;

    $obj2->color = 'metallic black';
    $obj2->topSpeed = 140;
}
}



// We can simply utilise a property which is not initialised in class structure. and surprisingly PHP will not give errors.

ex:
{{

$obj2->wheels = 5; 
echo $obj2->wheels;                                                                                               

}}






// Introducing methods:


class Item{
    //properties
    name;
    live;

    //methods or actions
    function walk(){
        echo 'huehuehue';
    }

    function run(){
        echo 'hue';
    }
}

// access methods also using -> thin arrow operator

$obj1 = new Item();
$obj1->walk();
$obj1->run();

$




 
 
 `Introducing $this keyword` : $this keyword refers to the the object who had it.
 ex: 
 
 class person{

    $name = "JP";
    $age = 0;

    function myName(){
        return $this->name;
    }

    function myAge(){
        return $this->age;
    }

 }

 $aditya = new person();
 $aditya->name = "aditya JP";

 echo $aditya->myName();   
// here myName is called by object aditya therefore in the fxn $this will contain instance of aditya object.








`Constructor`
Constructor is a method i.e. called everytime when a new instance is created of a class .
It is defined inside class body using a keyword `__construct`.
syntax:
{{
    
    class person{

        function __construct(){
            echo 'huehuehue';
        }

    }
}}




`Parameterized Constructor`
At the time of object creation we can pass parameters to it. the parameters are then parceled to constructor and there we can assign values.
ex: 

{{

    class Person{

        $name;
        $age;

        function __construct( $name, $age ){
            
            $this->$name = $name;
            $this->$age = $age;

        }


    }

    // passing params
    $monty = new Person("MontyJP", 26 );
    echo $monty->name;
    echo $monty->age;
}}





`Access Control : private`

The private keyword restricts the access of any property/action outside from the class that means we can access private variables/functions only inside the class. 

ex:
{{

    class Person{

        private name = "bunty";
        public age = 20;

        function myName(){
           echo $this->$name;              // Can Do 
        }

    }

    $bunty = new Person();

    echo $bunty->name;                   // Can't Do 
}}


// What if we need to get or set any private value outside from the class?
There we will use getter/setter.
ex:

{{

    class Person{

        private name = "bunty";
        public age = 20;

        public function getName(){
           return $this->$name;            
        }

        public function setName($name){
            $this->$name = $name;
        }

    }
}}





`static properties`

The property which is not object specific but class specific. 
static properties have a single instance for a single class.
We can access static property even without instantiating any object.( obv. because it is not related with object )
it is declared using static keyword;

ex:
{{

    class Person{

        public static $yearInLiving = 2023;

        ... // properties
        
        ... // actions

        //Access inside the class

        function __construct(){
            static::$yearInLiving += 1;
        }
    }

    // Access outside the class

    echo Person::$yearInLiving;                    // 2023

    $aditya = new Person();
    echo Person::$yearInLiving;                    // 2024
    
    $monty = new Person();
    echo Person::$yearInLiving;                    // 2025

}}           






// Creating Constants 

<-> While defining constants we don't use `$` symbol;

`Using define():`

{{
    define( "PI", 3.142 );

    // ACCESS
    echo PI;
}}

These constants are having global scope in the program. i.e. We can access them from anywhere in program once they are declared.
One disadvantage is -<> we can't use define() inside a class;


`const keyword`
To define a constant in class we simply use const keyword;
ex; {{

    class Person{

        public const PI = 3.1428;
    }

    // access it outside a class
    echo Person::PI;
}}







` INHERITANCE `
The process where all the properties and actions of a class can be transferred to another class without writing the whole code.
KEYWORD:  extends 

{{

    class A {

        $property1 = 1;
        $property2 = 2;

        function action1(){
            echo "HUEHUEHUE";
        }
    }
 
    class B extends A {                        // Inheritance
        $property3 = 3;
    }

    $objOne = new B();

    echo $objOne->$property1;
    echo $objOne->$property2;
    echo $objOne->$property3;

    $objOne->action1();                                 
$
}}






`Method Overriding :`
When a class redefine a method which was already defined in its parent class is called method overriding.
now in future if the fxn is called then the updated fxn will be executed.
ex: 

{
    class A {
        $name = "JP";
        $age = 20;

        function getInfo(){
            return "Name: " . $this->$name . " is " . $this->$age  . " years old !";
        }
    }

    class B{

        $salary = "50k";                                                                                          $

       // Method Overriding
        function getInfo() {
            echo parent::getInfo() . " having salary of " . $salary ;
        }

        // parent::getInfo() will call the parent function
    }

}





`Access control presents : protected`
=> We stuck in a situation when we need a private variable in its child class but also not allowed outside the class, Introducing PROTECTED: it allows a variable to be accessible in a own class and its child class but not allowed else anywhere.

ex: {

    class A {

        protected $a = "huehuehue";
    }

    class B extends A {

        function __construct(){
            echo $a + ' dogesh !';
        }
        
    }
}





