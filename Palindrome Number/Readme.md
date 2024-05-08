# Palindrome Number
## Difficulty: Easy

### Description:
Given an integer *x*, return *true* if *x* is palindrome integer.  
An integer is a **palindrome** when it reads the same backward as forward.
#### Examples:
>Input: x = 121  
Output: true  
Explanation: 121 reads as 121 from left to right and from right to left.

>Input: x = -121  
Output: false  
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

>Input: x = 10  
Output: false  
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

#### Constraints:

+ -2^31 <= x <= 2^31 - 1

#### Follow-up:
Could you solve it without converting the integer to a string?

___

### Solution(s):
1. Convert to string   
Time complexity: O(n)   
Space complexity: O(1)
```
set String_number = string of x
set String_rebmun = empty
for i from count of digits of x to 0  do:
	String_rebmun = String_number[i]
if String_number is euqal to String_rebmun then return true, if not return false
```
**If instead of whole number we loop over half of that this algorithm could be improved to O(n/2)**  
But one must aware of count of integers in x, if that is odd remove the last charater (middle one in the original input).

2. Revert half of the number  
Time complexity: O(log10(n))   
Space complexity: O(1)
```
if x is lower than 0 return false
if x is lower than 10 and greater than or equal to zero return true
if x mod 10 is euqal to 0 return false
set Int_rebmun = 0
while x is greater than Int_rebmun do:
	set Int_rebmun = ((Int_rebmun * 10) + (Int_rebmun mod 10))
	set x = x / 10
if x is equal to Int_rebmun or x is equal to (Int_rebmun / 10) then return true otherwise return false
```
The last condition will check if number of digits of x is odd number e.g: 101, 1235321
## C-Sharp  
```
static bool IsPalindrome_ConvertToString(int x) {
	string number = x.ToString();
	string rebmun = "";
	for (int i= number.Length - 1;i>-1;i--)
	    rebmun += number[i];
	return number == rebmun;
}
        
        
static bool IsPalindrome_RevertHalfOfTheNumber(int x) {
	if (x < 0) return false;
	if (x < 10 && x >= 0) return true;
	if (x % 10 == 0) return false;
	int Int_rebmun = 0;
	while (x > Int_rebmun)
	{
		Int_rebmun = ((Int_rebmun * 10) + (x % 10));
		x = x / 10;
	}
	return x == Int_rebmun || x == Int_rebmun / 10;
}
```
## Javascript  
```
const IsPalindrome_ConvertToString = x => {
    let x_string = x.toString();
    let rebmun = "";
    for (let i = x_string.length - 1; i > -1; i--)
        rebmun += x_string[i];
    return x_string === rebmun;
};


const IsPalindrome_RevertHalfOfTheNumber = x => {
    if (x < 0) return false;
    if (x < 10 && x >= 0) return true;
    if (x % 10 == 0) return false;
    let Int_rebmun = 0;
    while (x > Int_rebmun) {
        Int_rebmun = (Math.floor(Int_rebmun * 10) + Math.floor(x % 10));
        x = Math.floor(x / 10);
    }
    return x == Int_rebmun || x == Math.floor(Int_rebmun / 10);
};
```
## C++
```
#include<string>

const  bool IsPalindrome_ConvertToString(const int x) {
	std::string number = std::to_string(x);
	std::string  rebmun = "";
	for (int i= number.length() - 1;i>-1;i--)
	    rebmun += number[i];
	return number == rebmun;
}

const bool IsPalindrome_RevertHalfOfTheNumber(int x) {
	if (x < 0) return false;
	if (x < 10 && x >= 0) return true;
	if (x % 10 == 0) return false;
	int Int_rebmun = 0;
	while (x > Int_rebmun)
	{
		Int_rebmun = ((Int_rebmun * 10) + (x % 10));
		x = x / 10;
	}
	return x == Int_rebmun || x == Int_rebmun / 10;
}
```
## PHP
```
function IsPalindrome_ConvertToString($x) {
     $x_string =strval($x);
	 $rebmun = "";
    for ($i = strlen($x_string) - 1; $i > -1; $i--)
        $rebmun .= $x_string[$i];
    return $x_string === $rebmun;
}

//PHP < 7
function IsPalindrome_RevertHalfOfTheNumber($x){
    if ($x < 0) return false;
    if ($x < 10 && $x >= 0) return true;
    if ($x % 10 == 0) return false;
    $Int_rebmun = 0;
    while ($x > $Int_rebmun) {
        $Int_rebmun = floor($Int_rebmun * 10) + ($x % 10);
        $x = floor($x / 10);
    }
    return $x === $Int_rebmun || $x === floor($Int_rebmun / 10);
}

// PHP > 7
function IsPalindrome_RevertHalfOfTheNumber($x){
    if ($x < 0) return false;
    if ($x < 10 && $x >= 0) return true;
    if ($x % 10 == 0) return false;
    $Int_rebmun = 0;
    while ($x > $Int_rebmun) {
        $Int_rebmun = $Int_rebmun * 10 + ($x % 10);
        $x = intdiv($x,10);
    }
    return $x === $Int_rebmun || $x === intdiv($Int_rebmun,10);
};
```