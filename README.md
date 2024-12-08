EXPERIMENT NO. 04

Title:	OOP concepts in PHP
Aim: To understand and Apply the Object Oriented Concepts  in PHP Language. 
Objective: To implement the program on OOP Concepts in PHP
Contents:
	Creating Class and Objects
	Accessing member function
	Access Specifiers in PHP
	Constructor 
	Encapsulation
	Inheritance
	Interface 
	Abstract Class

Problem Statements to perform in lab:
Problem Stmt1 : Class, Object and constructor 
 



<?php
class Holiday
{
    private String $name;
    private int $day;
    private String $month;
    function __construct($name, $day, $month)
    {
        $this->name = $name;
        $this->day = $day;
        $this->month = $month;
    }
    function insamemonth($holiday2)
    {
        return $this->month == $holiday2->month;
    }
}
$holiday1 = new Holiday('DS', 15, 'Aug');
$holiday2 = new Holiday('ABC', 10, 'Aug');

if ($holiday1->insamemonth($holiday2)) {
    echo "The holidays are in Same month";
} else {
    echo "The holidays are not in same month";
}
?>










Problem Stmt2 : Inheritance
Base class Parent with static variable bank_balance=1000 and two methods i.e Deposit() and Withdraw(). 
Method implementation is two argument, no return type where the money value is either deposited or withdraw from bank_balance. 
Create  child classes i.e Son inherits the Parent class.
Create the 2 object and call methods Deposit() and Withdraw() 
Check final bank balance at end. ( as per ur Deposit() and Withdraw)
<?php
class Bank{
    public static $bank_balance = 1000;
    function Deposit($amt){
        self::$bank_balance += $amt;
    }
    function withdraw($amt){
        self::$bank_balance -= $amt;
    }
}
class Son extends Bank{
    // Inherits methods from Parent class
}

$son1 = new Son();
$son1->Deposit(1000);
$son1->withdraw(500);
echo "Final bank balance: " . Bank::$bank_balance . "\n";
?>









Problem Stmt3 : Abstract Class
Create an abstract class named Fruit,    3 child classes extending the abstract class namely: Apple, Orange, Grape. In these child classes, define the color function so that it prints Apple is red for the Apple class, Orange is orange for the Orange class and Grape is purple for the Grape class.
<?php
abstract class Fruit {
    protected $name;
    public function __construct($name) {
        $this->name = $name;
    }
    abstract public function color();
}

class Apple extends Fruit {
    public function color() {
        echo $this->name . " is red.\n";
    }
}

class Orange extends Fruit {
    public function color() {
        echo $this->name . " is orange.\n";
    }
}

class Grape extends Fruit {
    public function color() {
        echo $this->name . " is purple.\n";
    }
}

$apple = new Apple("Apple");
$orange = new Orange("Orange");
$grape = new Grape("Grape");

$apple->color();  
$orange->color(); 
$grape->color();  
?>



Problem Stmt4 : Interface
Write a PHP class called 'Shape' with an abstract method 'calculateArea()'. Create two subclasses, 'Triangle' and 'Rectangle', that implement the 'calculateArea()' method.
<?php
interface Shape
{
    public function calculateArea();
}
class Triangle implements Shape
{
    private $base;
    private $height;

    public function __construct($base, $height)
    {
        $this->base = $base;
        $this->height = $height;
    }
    public function calculateArea()
    {
        return 0.5 * $this->base * $this->height;
    }
}
class Rectangle implements Shape
{
    private $width;
    private $height;

    public function __construct($width, $height)
    {
        $this->width = $width;
        $this->height = $height;
    }
    public function calculateArea()
    {
        return $this->width * $this->height;
    }
}
$triangle = new Triangle(10, 5);
echo "Area of the triangle: " . $triangle->calculateArea() . "<br>";

$rectangle = new Rectangle(10, 5);
echo "Area of the rectangle: " . $rectangle->calculateArea();

////////////////////////////////////////////////////////////////////////////////


Problem Statement:
Create a registration form with all component (Textbox, radio button, checkbox, list..) . Perform the validation of all fields. After Submit Display information of registration in PHP on other page
(Make use of POST method, Use Superglobal variable $_POST() 
Fields: Roll, Name, Class (List) Email ID, Phone Number, Gender (radio), Technology Known (Checkbox) etc…
(Include all kind of components in form)


1.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body style="display: flex; justify-content: center; align-items: center;">

    <div class="container">
        <h2>Registration form </h2>
        <form action="action.php" method="POST">
            First Name : <input type="text" name="fname" required><br><br>
            Last Name : <input type="text" name="lname" required><br><br>
            Roll Number : <input type="text" name="roll" required><br><br>
            Email : <input type="text" name="email" required><br><br>
            Password : <input type="password" name="password" required><br><br>
            Enter Mobile Number : <input type="text" name="monumber" required><br> <br>  

            Gender : <input type="radio" name="gender" value="Male"> Male
            <input type="radio" name="gender" value="Female"> Female<br><br>
            
            <label for="class">Class:</label>
            <select id="class" name="class" required>
                <option value="SY">SY</option>
                <option value="TY">TY</option>
                <option value="BTech">BTech</option>
            </select><br><br>

            <label>Technology Known:</label>
                <input type="checkbox" id="html" name="technology[]" value="HTML">HTML
            
                <input type="checkbox" id="css" name="technology[]" value="CSS">CSS
                
                <input type="checkbox" id="php" name="technology[]" value="PHP">PHP

                <br><br>


            <input type="submit" name="submit" value="Submit" >


        </form>
    </div>
</body>
</html>


///////////////////////

action.php


<!DOCTYPE html>
<html>

<head>
    <title>Registration Details</title>
</head>

<body style="display: flex; justify-content: center; align-items: center;">

    <div class="container">
        <h2>Registration Details</h2>
        <?php
        if (isset($_POST['submit'])) {
            $fname = $_POST['fname'];
            $lname = $_POST['lname'];

            $roll = $_POST['roll'];
            $email = $_POST['email'];


            $password = $_POST['password'];

            $monumber = $_POST['monumber'];
            $class = $_POST['class'];
            $gender = $_POST['gender'];
            $technology = $_POST['technology'];


            if (!preg_match('/^[a-zA-Z]+$/', $fname)) {
                echo "<p>First Name: Invalid First name</p>";
            } else {
                echo "<p>First Name: $fname</p>";
            }

            if (!preg_match('/^[a-zA-Z]+$/', $lname)) {
                echo "<p>Lirst Name: Invalid Last name</p>";
            } else {
                echo "<p>Lirst Name: $lname</p>";
            }

            if (!preg_match('/^[0-9]{7}+$/', $roll)) {
                echo "<p>Roll Number: Invalid Roll Number</p>";
            } else {
                echo "<p>Roll Number: $roll</p>";
            }

            if (!preg_match('/^[1-9][0-9]{9}+$/', $monumber)) {
                echo "<p>Mobile Number: Invalid Mobile Number</p>";
            } else {
                echo "<p>Mobile Number: $monumber</p>";
            }

            if (!preg_match('/^[a-zA-Z0-9_]{8,}+$/', $password)) {
                echo "<p>Password : Invalid Mobile Number</p>";
            } else {
                echo "<p>Password: $password</p>";
            }

            if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
                echo "<p>Email ID: Invalid email address</p>";
            } else {

                echo "<p>Email ID: $email</p>";
            }


            echo "<p>Class: $class</p>";
            echo "<p>Gender: $gender</p>";
            echo "<p>Technology Known: " . implode(", ", $technology) . "</p>";
        }
        ?>
    </div>
</body>

</html>



