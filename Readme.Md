# HTML Interview Questions 

- What is HTML?
HTML (HyperText Markup Language) is the standard language for creating web pages.

Syntax:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```


- Difference between HTML and HTML5?
    + HTML5 is the modern, standardized evolution of HTML that adds native multimedia, semantic elements, new form controls, graphics APIs, and offline/storage features while keeping backward compatibility with older HTML; use HTML5 for any new web project because it’s supported by all modern browsers and mobile devices worldwide
    - Doctype and parsing: HTML5 uses a single, simple doctype <!DOCTYPE html> which standardizes parsing across browsers and reduces quirks.
    - Semantics and accessibility: HTML5 introduces semantic elements (<header>, <nav>, <main>, <article>, <section>, <footer>) that improve document structure, SEO, and screen‑reader behavior.
    - Multimedia without plugins: HTML5 provides native <audio> and <video> elements so sites no longer need third‑party plugins like Flash.
    - Graphics and interactivity: The <canvas> element and integrated SVG let you draw 2D graphics and animations directly in the browser.
    - Enhanced forms and validation: New input types (email, tel, date, number, url, search) and client‑side validation reduce JavaScript boilerplate.
    - APIs for modern apps: HTML5 added Web Storage (local/session), Offline AppCache/Service Workers, Geolocation, Web Workers, Drag & Drop, enabling richer single‑page and offline experiences
    
    ```
    <!-- HTML4 way -->
    <div id="header"></div>

    <!-- HTML5 way -->
    <header>
    <h1>Website Title</h1>
    </header>

    <!-- HTML5 multimedia -->
    <video controls>
    <source src="movie.mp4" type="video/mp4">
    </video>

    ```
+  Block vs Inline Elements

```
<!-- Block element: takes full width -->
<div style="background: lightblue;">This is a block</div>

<!-- Inline element: fits content -->
<span style="color: red;">This is inline</span>
```

#### How to make download option using HTML
+ We can achieve this by using element `<a>` and the attribute `download`
```html
<a href="file_name_to_download.pdf" download>  Download the file </a>
```

#### What is the importance of the attribute `autocomplete`
+ By using `autocomplete` attribute, we can make browser to suggest things you typed before. We can turn it `on` or `off`
```html
<input type="text" name="email" autocomplete="on" />
```

Log in
Sign up for free
function demo(){
    let name="ddd";
    function demo1(){
        return name
    }
    demo1()


}

console.log(demo())
Correct above program for closure concept

To demonstrate the closure concept in JavaScript, you need to return the inner function's result from the outer function.

Corrected program
```
function demo() {
    let name = "ddd";

    function demo1() {
        return name;
    }

    return demo1();
}

console.log(demo()); // Output: ddd
```
How closure works
-----------------

- demo() creates a local variable name with the value "ddd".
- demo1() is an inner function that accesses the outer function's variable name.
- return demo1() returns the result of the inner function.
- console.log(demo()) prints "ddd".

- A better example to understand closures

```
function demo() {
    let name = "ddd";

    function demo1() {
        return name;
    }

    return demo1;
}

let result = demo();

console.log(result()); // ddd
```

Important difference:

- return demo1() → Returns the result of executing the inner function.
- return demo1 → Returns the inner function itself.
- The second example demonstrates closure more clearly because the inner function is returned and can still access the outer function's variable even after the outer function has finished executing.

- Get better writing help
- Log in for more personalized help with writing, rewriting, and translation.


Log in
------

- Sign up for free
```
function demo(str){
   let freq={};
   for(let i of str){
    if(freq[i]){
        freq[i]++
    }
    else{
        freq[i]=1
    }
   }

   return freq



}
let str="asfassafasfASkfglh"

console.log(demo(str))explain logic
```
- Your program counts how many times each character appears in a string. This is called Character Frequency Counter in JavaScript.

Let's understand it step by step.

1. Your code

javascript
function demo(str) {
    let freq = {};

    for (let i of str) {
        if (freq[i]) {
            freq[i]++;
        } else {
            freq[i] = 1;
        }
    }

    return freq;
}

let str = "asfassafasfASkfglh";

console.log(demo(str));
2. Explain the logic step by step
Step 1: Create an empty object


javascript
let freq = {};
Initially, the object is empty.

We use this object to store each character and its count.

Step 2: Loop through the string


javascript
for (let i of str)
The for...of loop takes each character from the string one by one.

For example:


javascript
let str = "apple";
Loop execution:

First iteration: i = "a"

Second iteration: i = "p"

Third iteration: i = "p"

Fourth iteration: i = "l"

Fifth iteration: i = "e"

Step 3: Check whether the character already exists


javascript
if (freq[i]) {
    freq[i]++;
} else {
    freq[i] = 1;
}
This is the main logic.

If the character already exists in the object, increase its count by 1.

If the character does not exist, create a new property and assign 1.

3. Dry run example
Let's take:


javascript
let str = "apple";
Character (i)

Condition

Object (freq)

a

New character

{a: 1}

p

New character

{a: 1, p: 1}

p

Already exists, increment

{a: 1, p: 2}

l

New character

{a: 1, p: 2, l: 1}

e

New character

{a: 1, p: 2, l: 1, e: 1}

4. Final output
For your input:


javascript
let str = "asfassafasfASkfglh";
The output is:


javascript
{
  a: 3,
  s: 5,
  f: 4,
  A: 1,
  k: 1,
  g: 1,
  l: 1,
  h: 1
}
Note: JavaScript is case-sensitive, so a and A are counted separately.

5. Important concept to remember
The most important line is:


javascript
freq[i] = (freq[i] || 0) + 1;
You can replace your entire if-else block with this single line.

Your simplified program:


javascript
function demo(str) {
    let freq = {};

    for (let i of str) {
        freq[i] = (freq[i] || 0) + 1;
    }

    return freq;
}

console.log(demo("apple"));
Output:


javascript
{ a: 1, p: 2, l: 1, e: 1 }
Interview tip: Character frequency counting is a common JavaScript coding interview question. Understand how objects work as key-value pairs, especially freq[i], because this is the core logic.


freq[i] = (freq[i] || 0) + 1; what is this

This line is a shortcut for your if-else condition:


javascript
freq[i] = (freq[i] || 0) + 1;
Let's break it down into simple steps.

1. What does freq[i] mean?
It accesses the value of a character in the freq object.

For example:


javascript
let freq = {
    a: 2,
    b: 1
};

console.log(freq["a"]); // 2
console.log(freq["b"]); // 1
console.log(freq["c"]); // undefined
If the character doesn't exist, JavaScript returns undefined.

2. What does || 0 mean?
The || operator is called the logical OR operator.


javascript
freq[i] || 0
It means:

If freq[i] has a truthy value, use that value.

Otherwise, use 0.

Examples:

| Expression | Result |
|---|---:|
| 2 || 0 | 2 |
| 5 || 0 | 5 |
| undefined || 0 | 0 |
| 0 || 0 | 0 |
| null || 0 | 0 |

3. How does the complete line work?

javascript
freq[i] = (freq[i] || 0) + 1;
Let's take this string:


javascript
let str = "aab";
First iteration: i = "a"


javascript
freq["a"] = (undefined || 0) + 1;
Result:


javascript
freq = { a: 1 };
Second iteration: i = "a"


javascript
freq["a"] = (1 || 0) + 1;
Result:


javascript
freq = { a: 2 };
Third iteration: i = "b"


javascript
freq["b"] = (undefined || 0) + 1;
Result:


javascript
freq = { a: 2, b: 1 };
4. Compare both approaches
Your original code:


javascript
if (freq[i]) {
    freq[i]++;
} else {
    freq[i] = 1;
}
Shortcut:


javascript
freq[i] = (freq[i] || 0) + 1;
Both perform the same character-counting logic for this example.

Remember this simple formula:

freq[i] → Get existing count.

|| 0 → If no count exists, take zero.

+ 1 → Increase count by one.

freq[i] = → Store the updated count.

This is a very useful JavaScript pattern for coding interviews!


What is WCAG 2.1?
WCAG 2.1 stands for Web Content Accessibility Guidelines 2.1.

It is a set of international guidelines that explain how to make websites and web applications accessible to everyone, including people with disabilities.

In simple words:

WCAG 2.1 helps developers build websites that people can use even if they have:

Visual impairments (blindness, low vision, color blindness).

Hearing impairments.

Physical disabilities (difficulty using a mouse or keyboard).

Cognitive or learning disabilities.

WCAG is developed by the W3C (World Wide Web Consortium).

Four main principles of WCAG
WCAG follows four important principles, commonly called POUR.

GMU ADA Title II Plan
 
1. Perceivable

Users must be able to perceive the information.

Example: Add alternative text (alt) to images so screen readers can describe them.

 
2. Operable

Users must be able to operate the website.

Example: All buttons, links and menus should work using a keyboard without a mouse.

ACCESSIBLE WEBSITES AND THE PUBLIC SECTOR
 
3. Understandable

Website content and functionality should be easy to understand.

Example: Forms should have clear labels and understandable error messages.

What is Cross-Browser and Multi-Platform Compatibility?
 
4. Robust

Website content should work with different browsers and assistive technologies.

Example: Use proper HTML elements and semantic tags.

