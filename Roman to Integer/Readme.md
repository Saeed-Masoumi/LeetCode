# Roman to Integer
## Difficulty: Easy

### Description:
Roman numerals are represented by seven different symbols: *I*, *V*, *X*, *L*, *C*, *D* and *M*.
>Symbol Value  
I 1  
V 5  
X 10  
L 50  
C 100  
D 500  
M 1000  

For example, *2* is written as *II* in Roman numeral, just two one's added together. *12* is written as *XII*, which is simply *X* + *II*. The number *27* is written as *XXVII*, which is *XX* + *V* + *II*.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not *IIII*. Instead, the number four is written as *IV*. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as *IX*. There are six instances where subtraction is used:  
+ *I* can be placed before *V* (5) and *X* (10) to make 4 and 9.  
+ *X* can be placed before *L* (50) and *C* (100) to make 40 and 90. 
+ *C* can be placed before *D* (500) and *M* (1000) to make 400 and 900.  
Given a roman numeral, convert it to an integer.
#### Examples:
>Input: s = "III"  
Output: 3  
Explanation: III = 3.

> Input: s = "LVIII"  
Output: 58  
Explanation: L = 50, V= 5, III = 3.

>Input: s = "MCMXCIV"  
Output: 1994  
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

#### Constraints:

+ 1 <= s.length <= 15  
+ s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M').  
+ It is guaranteed that s is a valid roman numeral in the range [1, 3999].  
#### Follow-up:
*Nothing to add.*

___

### Solution(s):
1. Left to Right   
Time complexity: O(1)   
Space complexity: O(1)
```
total = 0
letter_index = 0
while i letter_index s.length do:
    if at least 2 symbols remaining AND value of s[letter_index] < value of s[letter_index + 1]:
        total = total + (s[letter_index + 1]) - (s[letter_index])  
        letter_index = letter_index + 2
    else:
        total = total + s[letter_index]
        letter_index = letter_index + 1
return total
```
**This algorithm can be improved if one take 13 symbols as roman symbols istead of 7 symbols (like CM,CD,XC,...). But complexities will remain as same as before**  
2. Right to Left  
Time complexity: O(1)   
Space complexity: O(1)
```
last = s.length - 1
total = value(last)
for letter_index from count of elements of s -1 to 0 do:
    if value(s[letter_index]) < value(s[letter_index+1]):
        total -= value(s[letter_index])
    else:
        total += value(s[letter_index])
return total

```
## C-Sharp  
```
//We can use dictionary aka map for stroing symbols and their values
//or we can get value of symbol by calling an extera function.
//I will use the second approach
//C# >= 8
int GetValue(char symbol)
{
    return symbol switch
    {
        'I' => 1,
        'V' => 5,
        'X' => 10,
        'L' => 50,
        'C' => 100,
        'D' => 500,
        'M' => 1000,
        _ => 0,
    };
}

int RomanToInt_Left_to_Right(string s){
	int sum = 0;
	int i = 0;
	while (i < s.Length)
	{
	    int currentValue = GetValue(s[i]);
	    int nextValue = 0;
	    if (i + 1 < s.Length)
	        nextValue = GetValue(s[i+1]);
	    if (currentValue < nextValue)
	    {
	        sum += (nextValue - currentValue);
	        i += 2;
	    }
	    else
	    {
	        sum += currentValue;
	        i += 1;
	    }
	}
	return sum;
}

int RomanToInt_Right_to_Left(string s){
	int lastValue = GetValue(s[^1]);
	int total = lastValue;
	for (int i = s.Length - 2; i >= 0; i--)
	{
	    int currentValue = GetValue(s[i]);
	    if (currentValue < lastValue)
	        total -= currentValue;
	    else
	        total += currentValue;
	    lastValue = currentValue;
	}
	return total;
}
```
## Javascript  
```
const GetValue = c => {
    switch (c) {
        case 'I': return 1;
        case 'V': return 5;
        case 'X': return 10;
        case 'L': return 50;
        case 'C': return 100;
        case 'D': return 500;
        case 'M': return 1000;
    }
    return 0;
};

const RomanToInt_Left_to_Right = s => {
    let sum = 0;
	let i = 0;
    while (i < s.length) {
	    let currentValue = GetValue(s[i]);
	    let nextValue = 0;
        if (i + 1 < s.length)
            nextValue = GetValue(s[i + 1]);
        if (currentValue < nextValue) {
            sum += (nextValue - currentValue);
            i += 2;
        }
        else {
            sum += currentValue;
            i += 1;
        }
    }
    return sum;
};

const RomanToInt_Right_to_Left = s => {
    let lastValue = GetValue(s.slice(-1));
	let total = lastValue;
	for (let i = s.length - 2; i >= 0; i--)
	{
	    let currentValue = GetValue(s[i]);
	    if (currentValue < lastValue)
	        total -= currentValue;
	    else
	        total += currentValue;
	    lastValue = currentValue;
	}
	return total;
};
```
## C++
```
#include <iostream>
#include <string>
#include <cstring>

const int GetValue(const char symbol)
{
	switch (symbol)
	{
	case 'I':
		return 1;
	case 'V':
		return 5;
	case 'X':
		return 10;
	case 'L':
		return 50;
	case 'C':
		return 100;
	case 'D':
		return 500;
	case 'M':
		return 1000;
	default:
		return 0;
	}
}

const int RomanToInt_Left_to_Right(const char *s)
{
	int sum = 0;
	int i = 0;
	while (i < std::strlen(s))
	{
		int currentValue = GetValue(s[i]);
		int nextValue = 0;
		if (i + 1 < std::strlen(s))
			nextValue = GetValue(s[i + 1]);
		if (currentValue < nextValue)
		{
			sum += (nextValue - currentValue);
			i += 2;
		}
		else
		{
			sum += currentValue;
			i += 1;
		}
	}
	return sum;
}

const int RomanToInt_Right_to_Left(const char *s)
{
	int lastValue = GetValue(s[std::strlen(s) - 1]);
	int total = lastValue;
	for (int i = std::strlen(s) - 2; i >= 0; i--)
	{
		int currentValue = GetValue(s[i]);
		if (currentValue < lastValue)
			total -= currentValue;
		else
			total += currentValue;
		lastValue = currentValue;
	}
	return total;
}
```
## PHP
```
function GetValue($symbol)
{
    switch ($symbol) {
        case 'I':
            return 1;
        case 'V':
            return 5;
        case 'X':
            return 10;
        case 'L':
            return 50;
        case 'C':
            return 100;
        case 'D':
            return 500;
        case 'M':
            return 1000;
        default:
            return 0;
    }
}

function RomanToInt_Left_to_Right($s)
{
    $sum = 0;
    $i = 0;
    while ($i < strlen($s)) {
        $currentValue = GetValue($s[$i]);
        $nextValue = 0;
        if ($i + 1 < strlen($s))
            $nextValue = GetValue($s[$i + 1]);
        if ($currentValue < $nextValue) {
            $sum += ($nextValue - $currentValue);
            $i += 2;
        } else {
            $sum += $currentValue;
            $i += 1;
        }
    }
    return $sum;
}

function RomanToInt_Right_to_Left($s)
{
    $lastValue = GetValue(substr($s, -1));
    $total = $lastValue;
    for ($i = strlen($s) - 2; $i >= 0; $i--) {
        $currentValue = GetValue($s[$i]);
        if ($currentValue < $lastValue)
            $total -= $currentValue;
        else
            $total += $currentValue;
        $lastValue = $currentValue;
    }
    return $total;
}
```