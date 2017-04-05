# Arrays

Let's say I want you to write a program that mimics a shopping list. It should have 30 items (represented by strings) and it should console.log each item in alphabetical order. How do we do that? I guess we could write some variables:

```
var apples = 'apples';
var bananas = 'bananas';
var cheese = 'cheese';
... (etc, etc, you get it)
```

And then maybe we could write some if statements? I guess? Uh, sounds like a ton of conditionals, and I'm not sure how... hmm... what if...

I don't think this program is going to work very well with the tools we currently have. We need a way to store a bunch of words together and keep track of their order. Maybe in some sort of list? Ah, what we need here is an **array**!

An array is just a list in your computer. Every 'slot' in the list acts like a variable. You can see what value a particular slot points to, and you can make the slot point to a different value if you need to. Let's take a look at some actual arrays:

```
[];
[5];
['Hello', 'Goodbye'];

var apples = 'apples'; // Obviously, this is not an array
[23.2, apples, [true, false]]; // But this is!
```

So, first we have an empty array, then an array holding a single number, then an array holding two strings. Next, we have a variable assignment (we've seen those before), then an array holding three values. The second value is our defined variable (we can put those in arrays too). The last element in this array is another array (That's right, we can put arrays inside of arrays! It's called **nesting**).

To help us find a particular value in an array, each slot is given an **index** number. Programmers (and, incidentally, most mathematicians) start counting each slot from zero, though. So the first slot in the array is slot zero. Here's how we would reference the values in an array:

Code:
```
var shopping = ['apples', 'bananas', 'cheese'];

console.log(shopping);
console.log(shopping[0]);
console.log(shopping[1]);
console.log(shopping[2]);
console.log(shopping[3]); // This is out of range. There is no value at index three of our shopping array.
```

Output:
```
['apples', 'bananas', 'cheese']
apples
bananas
cheese
undefined
```

So, we see that `console.log(shopping);` logs the whole array looking like how we initially defined it. Then we use `console.log(shopping[0]);` to log the "first" item in the array, and `console.log(shopping[1]);` to log the "second". I'm sure this seems confusing, but you do get used to it. You just have to really start thinking that counting begins at zero, and stop using words like "first" and "second".  If you go out to a five-course meal, don't talk about the "first" course; talk about course zero (and in your head, be thinking `course[0]`). You have five fingers on your right hand, and their numbers are 0, 1, 2, 3, and 4. You'll know you've got it when you start using the word "zeroth". Yes, it's a real word! Ask any programmer.

Finally, we tried `console.log(shopping[3]);`, just to see what would happen. Were you expecting an error? Sometimes when you ask a question, your question doesn't make sense (at least to your computer); that's when you get an error. Sometimes, however, you can ask a question and the answer is **nothing**. What's in slot three? **undefined**.

## Exercise Set One:

1. Create a variable named 'colors'. Set it to an array that holds the strings 'red', 'blue', and 'green'.
2. `console.log` the value at index 1 of the colors array.

## A Few More Basics

Let's say we have our shopping list array. Currently, it has 'apples', 'bananas', and 'cheese'. Yikes! I just remembered I'm allergic to apples! I need to change that to a different fruit... how about oranges? But how would we go about that?

Code:
```
var shopping = ['apples', 'bananas', 'cheese'];
shopping[0] = 'oranges';

console.log(shopping);
```

Output:
```
['oranges', 'bananas', 'cheese']
```

As you can see, we can **reassign** the value of certain slots by accessing their index, and then using our `=` operator to assign a new value. We can do the same thing with slots that are currently undefined:

Code:
```
var shopping = ['apples', 'bananas', 'cheese'];
shopping[5] = 'oranges';

console.log(shopping);
```

Output:
```
[ 'apples', 'bananas', 'cheese', , , 'oranges' ]
```

Previously, there was no element at slot 5 of our list, but now we have one! The output represents the 'empty' slots as whitespace divided by commas. Those slots are still 'undefined'.

The last important property to understand about arrays is the **length** property. The length property will tell us how long an array is.

Code:
```
var shopping = ['apples', 'bananas', 'cheese', 'oranges'];

console.log(shopping.length);
```

Output:
```
4
```

As you can see, appending `.length` to an array will return its length. The length of an array is counted like 'normal', so remember that even though 'oranges' is at the last defined slot, slot 3, this array still has a length of 4!

## Exercise Set Two:

1. Create a variable named 'colors'. Set it to an array that holds the strings 'red', 'blue', and 'green'.
2. Change 'blue' to be 'yellow'
3. Add an element at index 6 that contains another color.
4. console.log your new array
5. console.log the length of your array

# Built-In Array Methods

Like with strings, we have a ton of methods that JavaScript provides for us to use with arrays. We're not going to over them ALL here (that would take forever), but we'll cover a few of the most useful ones. If you're interested in learning about other array methods, head on over to [MDN's array page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) and check them out.

## Join

JavaScript's array join method "joins" all elements in an array into a single string. Take our shopping list as an example:

Code:
```
var shopping = ['apples', 'bananas', 'cheese'];
console.log(shopping.join());
```

Output:
```
applesbananascheese
```

[comment]: # Note on this section. There's a good chance we'll cover parameters earlier with either `console.log` or string methods, but I typed it out here for clarity's sake.


Neat! That might be a good way to log things sometimes. However, `applesbananascheese` isn't exactly the most readable thing is it? What if we want to put a space in between each word? Luckily, the join method takes a **parameter** or **argument** (these are synonymous terms, but we'll use parameter from now on for simplicity's sake). We'll get into these 'parameters' more later on, but essentially a parameter is the **input** that a method takes. In the join method's case, its parameter is a string. Take a look at this:

Code:
```
var shopping = ['apples', 'bananas', 'cheese'];
console.log(shopping.join(' '));
```

Output:
```
apples bananas cheese
```

Can you spot the difference from our last code snippet? Here, we are putting a string with a single blank space into the parentheses of our join method. In the parentheses is where we put values we want to input into a method. We'll go over how this actually works in later checkpoints, but for now, what you need to understand is that whatever string you feed join as a parameter will be inserted in between each element to create our final string. Here's a more fun example:

Code:
```
var shopping = ['apples', 'bananas', 'cheese'];
console.log(shopping.join(' :) '));
```

Output:
```
apples :) bananas :) cheese
```

## Exercise Set Three:
1. Defined a variable containing an array of four strings. You can name the variable whatever you'd like, and the strings can contain any words or phrases you'd like.
2. `console.log` joining the elements of the array together with one blank space in between them.
3. `console.log` joining the elements of the array together with whatever string you'd like to add!
4. Define a variable containing a string (any string). With this new variable as the **parameter** (input) of your join function, `console.log` joining the array together.

## Push, Pop, Shift, and Unshift

Push and pop are sort of opposites, like + and - are. Push adds a value to the end of your array, and pop removes the last element from the array. I like thinking of push as adding a new item to the bottom of a list, and pop as deleting it. Push takes your new item as a **parameter**. Pop takes no parameters at all.

Code:
```
var animals = ['cat', 'dog', 'iguana']; // Mixing it up here so you don't get too used to our shopping list
animals.push('snake');

console.log(animals);

animals.pop();

console.log(animals);
```

Output:
```
['cat', 'dog', 'iguana', 'snake']
['cat', 'dog', 'iguana']
```

Shift and unshift do the same thing as push and pop, but they do it to the front of the array rather than the end:

Code:
```
var animals = ['cat', 'dog', 'iguana'];
animals.shift('snake');

console.log(animals);

animals.unshift();

console.log(animals);
```

Output:
```
['snake', 'cat', 'dog', 'iguana']
['cat', 'dog', 'iguana']
```

## Exercise Set Four
1. Define a variable containing an array of four elements (any elements you'd like!). Add an element to the **end** of the array.
2. Now, take the same array and add two elements to the **beginning** of the array.
3. `console.log` the element at index 4 of the array.
3. Remove the last two elements from the array.
4. Remove the first element from the array.

# Assignment

- Learn about the [array `sort` method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) (for now, ignore the parts about the parameter `compareFunction`, just read the about the first example). What types of elements is `sort` good at sorting? Which types does it sort things differently than we might expect? Write an explanation and send it to your mentor.