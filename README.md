# PHP Test

## Task 1  `50b`

In some German federal states elections the parliamentary seats are distributed as follows. The seats allocated to a party are calculated by this method in two steps:

1. The corresponding number of votes that are attributable to a party is multiplied by the total number of available seats and divided by the total number of valid votes.
2. The result is split into the integer portion and the rest. The integer parts are attributed to the respective party as seats. The remaining seats are allocated to parties in the order of the size of the fractional portions.

Exemplary data (assuming all votes are valid):
- Total seats: `15`
- Votes: 
```php
[
	"A" => 15000, 
	"B" => 5400, 
	"C" => 5500,  
	"D" => 5550
]
```
**Result should be:**
```php
[
	"A" => 7, 
	"B" => 2, 
	"C" => 3, 
	"D" => 3
]
```
Detail: http://goo.gl/mtjTN7

**_Write a class that calculates  for a variable number of parties and seats and include the needed two lines how to call your class._**

----------
## Task 2  `3b`

Using a foreach loop to modify the array strings, make sure every item in the array $strings has an uppercase first letter (**use as little code as possible**):

```php
$strings = [
"name" => "bar",
"surname" => "tender",
"profession" => "developer at bileto",
"department" => "core",
];

var_dump(transform($string));
```

**_Create transform() function which will return:_**
```
array(4) {
  ["name"]=>
  string(3) "Bar"
  ["surname"]=>
  string(10) "Tender"
  ["profession"]=>
  string(19) "Developer at bileto"
  ["department"]=>
  string(4) "Core"
}
```

----------
## Task 3  `5b`

Please first **_explain the following piece of code_** and then **_change it to work without recursion_**.
```php
function doit($a, $b) {
	return ($b == 0) ? $a : doit($b, $a % $b);
}
var_dump(doit(1071, 1029));
```

----------
## Task 4  `6b`

```php
class SomeClass
{
	public function getValues($tool, $built, ...$par)
	{
    	// lets mock some data
    	$mocks = [[0, 1, 2, 17], [1, 2, 42, 96], [4, 5, 6, 7], [10, 13, 8, 15]];
    	foreach ($mocks as &$mock) {
        	    $mock = array_map(
                 function ($m) use ($par) {return $m * $par[1];}, $mock
              );
    	}
        	return $mocks;
	}
}

$a = ['php', 'ver 5.6', 3, 2];
$val = (new SomeClass)->getValues(...$a)[2][3];
```
Whats the value of $val after running the code?

**_Please rewrite the following working PHP 5.6 code in a way that it does exactly the same in PHP 5.3. Care for usage of memory and variables._** 

----------
## Task 5  `7b`

**_What is wrong or not well designed with the following working code in the method “isValidGoogleUser”?_**
Please judge it from a conceptional point of view.  Assume all referenced classes exist. There is NO syntax error an NO PHP error / problem. 

```php
class Model_Google {
	protected $_user = null;
	// … other properties

	/**
	* check if GoogleUser is valid
	* @return boolean
	**/
	public function isValidGoogleUser ($uid) {
		$this->_user = $this->_retrieveFromGoogle($uid);
		if ($this->_user instanceof  GoogleUser) {
		return true;
		} else {
			return false;
		}
	}

	/**
	* Retrieve User from Google with given user id
	* @returns GoogleUser || null
	**/
	private function _retrieveFromGoogle($uid) {
		// retrieve User from Google using $uid
		// some code …..
		return $googleUser;
	}

	// … other methods
}
```

----------
## Task 6  `7b`

In a flight simulator game we found the following classes:

```php
class Aircraft extends Wing {
	// some stuff
}

class Wing extends Flap {
	// some stuff
}

class Flap {
	// some stuff
}
```
Would you inherit in the same way or would you inherit in the opposite way or would you do anything totally different?
**_Please explain with a few words why and what!_**


----------
## Task 7  `8b`

There is one table `invest` with a self reference:

| id | parent_id | investor | investment | amount | last changed |
|:---:|:--- |:--- |:--- |:--- |:--- |:--- |
| 1 | null | 42 | 56| 1000 | 12.12.2014 |
| 2 | null | 43 | 12| 2000 | 15.12.2014 |
| 3 | 1 | 42 | 56 | 1500 | null |
| 4 | null | 44 | 12 | 1400 | null |
| 5 | 1 | 42 | 56 | 1600 | 10.12.2014 |
| 6 | 2 | 43 | 12 | 1200 | null |
| 7 | null | 42 | 56 | 1400 | 17.12.2014 |
| 8 | null | 42 | 56 | 1450 | null |

Valid/Current entities have parent_id null.

Every time a row becomes updated the old row values are stored in same table with parent_id of its original.
Every current investor / investment couple should be unique with the parent_id null like id 1, id 2, id 4. But there are several backups of changes allowed like id 3, id 5, id 6

Unfortunately there happened some wrong inserts like id 7, id 8 which is duplicate to id 1 and not allowed.

**_Write an MySQL statement that finds all investor/investment couples that have more than one entry with parent_id null_**

----------
## Task 8  `5b`

Think of a use case for either the Singleton or the Abstract Factory design pattern and **_write a few lines of code showing its class structure and also its interaction_** with other components.

----------
## Task 9  `2b`

**_What is the difference between foo() & @foo()?_**

----------
## Task 10  `7b`
**_Explain what the following working code snippet is doing (try in your php environment) and where do you see problems:_** 

```php
$subject = 'A Text <b>in bold</b> with <a href="/nextPage.php" title="next >Link" rel="/elsewhere.html">some content <img src="/images/default/next.png" style="extrawide" /></a>
<div class="box">5 px</div><a href="/zoo.php" title="Zoo"> Link to zoo <img src="/images/default/zoo.png" /></a> bla bla ';


$pattern = '~(<a.*?)(title=)(([\'"])([^\'"]*)(\4))([^>]*>)([^<]*)'
    . '(<img .*)(src=[\'"][^\'"]*[\'"])(.*?/>[^<]*</a>)~';
$replacement = '\1\7\8\9\10 alt="\5" \11';
$result = preg_replace($pattern, $replacement, $subject);
```
