---
layout: post
title:  "A DIVE IN SWIFT"
date:   2020-07-15 7:06:22 +0000
categories: All about Swift
---
# BASICS

In order to be proficient in a programming language, one has to read and write a lot of code written in it. This can not be done when you do not understand the language's basic syntax and keywords. 

We will be diving into swift to understand the symbols and keywords that are available to help you get started writing some swift code. 

Let’s get started!  

## Constants & Variables 
Constants and variables must be declared before use. You declare a constant with the `let` keyword and a variable with the `var` keyword. 

```
let length = 10  //Declares a constant
var width = 50 //Declares a variable 
```  

## Type Annotation 
You can declare a constant or variable with type annotation to be clear on the data of value it stores. 

```swift
var name: String
Name = "levit"
//Can be read as declare a variable of type String
```
This can also be written in a single line as; 
```swift
var name: String = "levit"
```
You can also declare multiple variables of the same type on a single line, separated by commas with a type annotation after the final variable name; 
```swift
var continent, country, city: String 
```
> It is rare to provide type annotation for variables and constants in practice. When you provide an initial value, swift will almost always infer the type of the variable or constant based on the value provided.”  

## Naming Variables & Constants
Variable and constant names can contain almost any character including unicode characters but can not contain whitespace characters, mathematical symbols, arrows. Nor can they begin with a number, though they can be included elsewhere within the name. 

## Printing Variables and Constants
Swift provides a `print(_:separator:terminator:)` function which can be used to print any value to an appropriate output.
```swift 
let language = "swift"
print(language)  //prints "swift" 
```  
Swift uses string interpolation to include variable and constant names as a placeholder in a longer string. To do this, wrap the name in parenthesis and escape it with a blacklash `\` before the opening parenthesis.
```swift 
print("I love \(language)") //prints "I love swift"
```

## Comments 
Use comments to add nonexecutable text in your code, as a reminder for yourself.  
Single line comments begin with two forward slashes `//`:  
```swift
//This is a single line comment
```  
Wrap multiline comments in `/* */`  
```swift
/*
this is 
a multiline
comment
*/
```

## DATA TYPES
* #### Integers
    * **Int**: holds whole numbers with no fractional components such as 30, -18.  
    `let age: Int = 20 //Declares an integer constant`
    * **UInt**: hold unsigned integers.  
    ```swift 
    var age: UInt = 20
    age = -20 //Results in a compiler error
    ```
* #### Floating-Point Numbers
    * **Float**: Represents a 32-bit floating-point number
    * **Double**: Represents a 64-bit floating-point number  
> Double has a precision of at least 16 decimal digits  
Float can be as little a 6 decimal digits 

* #### String
Represents a series of characters such as "hello, World". 

{% highlight swift %}
//For Single line string literal surround with single double quotation marks
let hello = "Hello, World" 

/* For Multiline String literal surround with three double quotation marks
Note: The string must begin on the first line after the opening quotation marks and end on the line 
before the closing quotation marks
*/
let greetings = """
The big brown fox
jumped over 
the lazy dog.
"""
{% endhighlight %}

* #### Bool
Represents data that can only be either true or false 
```swift
var isAmazing: Bool = true
let orangesAreBlue = false
```

## Tuples
Group multiple values into a single compound value. The values with in the tuple can be of any type and don't necessarily have to be of the same type

{% highlight swift %}
let info = ("swift" , 40.5)
//info is of type (String, Double) and equals ("swift", 40.5)
{% endhighlight %}

Accessing values in a tuple 
```swift
let langName = info.0
let value = info.1
```
Destructuring a tuple 
```swift 
let (a, b) = info
print(a) //prints "swift"
print(b) //prints 40.5
```

## Optionals
Optional are used to represent values that may be absent. Either there's a value, in which case it can be unwrapped to get the value or the value doesn't exist at all (`nil`).  
To declare a value as optional by placing a `?` after the value type 
{% highlight swift %}
var responseCode: Int? //Declares responseCode as an optional integer

//since responseCode is a variable (`var`)
responseCode = nil //sets it to contain no value

//OR 
responseCode = 200 //sets it to contain an integer value

{% endhighlight %}
> **Note:**  
{% highlight swift %}
/*
This will produce an error since the compile can't infer what type of optional it is 
*/
let optionValue = nil 
{% endhighlight %}

## Unwrapping Optionals 
* **Forced Unwrapping:**  
You can access the value in an optional by force unwrapping it. To force unwrap an optional, place an exclamation mark `!` after the variable or constant.
```swift
let statusCode = responseCode! //statusCode gets assigned to a non-optional integer
```
> **Note:**  
To force-unwrap an optional, you should be confident that the variable or constant contains a value else it will result in a runtime error.  

* **Optional Binding:**   
You can extract the value in an optional into a temporary constant or variable using an `if` statement. 
{% highlight swift %}
//Using if statement 
if let status = responseCode {
    // do something with the new status constant
}
{% endhighlight %}


## BASIC OPERATORS
#### Arithmetic 
* Addition: `+`
* Subtraction: `-`
* Multiplication: `*`
* Division: `/`
* Remainder: `%`

#### Comparison
* Equal to: `a == a`
* Not Equal: `a != b`
* Greater than: `5 > 3`
* Greater than or Equal: `5 >= 5`
> **Note**  
Swift provides two identity operators (`===`) & (`!==`) to test if two object references point to the same object instance.


#### Logical Operators 
* Not: `!a`
* And: `&&`
* Or: `||`

#### Ternary Condition Operator
The ternary operator is an operator with three parts which takes the form `condition ? action1 : action2.

{% highlight swift %}
let condition = true  //Declares a boolean constant

//using if statement
if condition {
    print("yay")
}else {
    print("Nay")
}

//Using the ternary operator 
condition ? print("yay") : print("Nay")

{% endhighlight %}

#### Nil-Coalescing Operator `??`
This operator unwraps an optional and returns its value if it contains any else it returns a default value you provide.  
It takes the form `optional value ?? default value`

{% highlight swift %}
//Using nil-coalescing
let value: Int? = nil

print(value ?? 10) //prints 10

{% endhighlight %}
> The nil-coalescing operator is the shorthand for
{% highlight swift %}
a != nil ? a! : b
//reads if a is not nil, return force-unwrapped a else return b
{% endhighlight %}  

#### Range Operators
* **Closed Range:**  
(a...b) defines a range that runs from a to b. The value of a must be greater than b.
{% highlight swift %}
for number in 1...5 {
    print(number)
}
//prints 1, 2, 3, 4, 5
{% endhighlight %} 

* **Half-Opened Range:**  
(a ..< b) defines a range that runs from a to b but doesn't include b.
 {% highlight swift %}
for number in 1..<5 {
    print(number)
}
print 1, 2, 3, 4
{% endhighlight %}

* **One-Sided Range:**
Defines a ranges that continues as far as possible in one direction
{% highlight swift %}
let languages = ["swift", "rust", "python", "javascript"]
for language in languages[...2]{
    print(language)
}
//prints "swift", "rust", "python"

for language in languages[1...]{
    print(language)
}
//prints "rust" , "python", "javascript"
{% endhighlight %}

## COLLECTION TYPES

### Arrays
Ordered collection of values. 
{% highlight swift %}
//Creating an empty array 
var languages = [String]()  //Creates an empty string array

//Creating an array with default values
let languages = ["swift", "rust", "python", "javascript"] //Creates a string array with default values

{% endhighlight %} 

**Accessing Array Elements**
{% highlight swift %}
//Creating an empty array 
let firstItem = languages[0]
let firstTwoItems = languages[0...1]
print(firstItem) //prints swift
print(firstTwoItems) //prints ["swift", "rust"]
{% endhighlight %} 

### Sets 
Unordered collections of unique values. Use sets instead of arrays when the order of items isn't important or when items are meant to appear only once. 
{% highlight swift %}
//Creating an empty set 
var usernames = Set<String>()

//creating a set with default values 
let usernames: Set<String> = ["levit", "kanner"]
{% endhighlight %} 

**Removing duplicates in an array**
{% highlight swift %}
let duplicates = [1, 2, 2, 1]
let noDuplicates = Array(Set(duplicates)) //creates a set from duplicates and converts it back to an array
print(noDuplicates) //prints [1, 2]
{% endhighlight %}


### Dictionaries
Dictionaries store unordered collections of key-value associations.
{% highlight swift %}
//Creating an empty dictionary 
var agesOfStudents = [String: Int]()  //Creates an empty [String: Int] dictionary
agesOfStudent["dan"] = 16  //agesOfStudents now contains 1 key-value pair

//Creating a dictionary with default values
let dict: [String : Int] = ["dan": 16, "king": 20, "sarah": 19]
{% endhighlight %}

**Accessing Dictionary Elements**
{% highlight swift %}
let danAge = dict["dan"]
print(danAge) //prints 16
{% endhighlight %}

## FLOW CONTROL
### For-In Loop
Use for-in loop to iterate over sequence such as arrays, ranges, characters in a string. You can also iterate over a dictionary to access its key-value pairs.
{% highlight swift %}
//Iterating over a range
for number in 1...5 {
    print(number)
}
//Iterating over a dictionary
let dict: [String : Int] = ["dan": 16, "king": 20, "sarah": 19]
for (name, age) in dict {
    print("\(name) is \(age) years old")
}
{% endhighlight %} 

### While Loops
While loops run as long as a condition holds. While loops come in two forms; while and repeat-while. 
* while evaluates its condition at the start of each pass through 
* repeat-while evaluates its condition at the end of each pass throught. It is therefore guaranteed to run at least once. 

**While**
{% highlight swift %}
var names = ["Dan", "King", "Sarah", "Hilson"]  //declared as variable for manipulation
while names.count > 1 {
    //Removes the last item from names as long as names.count is greater than 1
    let name = names.popLast()   
    print(name!)
}
{% endhighlight %}
**Repeat-while**
{% highlight swift %}
var names = ["Dan", "King", "Sarah", "Hilson"]
 repeat{
    //Removes the last item from names as long as names.count is greater than 1
    let name = names.popLast()   
    print(name!)
}while names.count > 1
{% endhighlight %}

