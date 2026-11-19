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
```
<input type="text" name="email" autocomplete="on" />
```


```
function demo(){
    let name="ddd";
    function demo1(){
        return name
    }
    demo1()


}

console.log(demo())
```
- Correct above program for closure concept

- To demonstrate the closure concept in JavaScript, you need to return the inner function's result from the outer function.

- Corrected program
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


- What is WCAG 2.1?
    - WCAG 2.1 stands for Web Content Accessibility Guidelines 2.1.
    - It is a set of international guidelines that explain how to make websites and web applications accessible to everyone, including people with disabilities.

- In simple words:

- WCAG 2.1 helps developers build websites that people can use even if they have: 
    - Visual impairments (blindness, low vision, color blindness).
    - Hearing impairments.
    - Physical disabilities (difficulty using a mouse or keyboard).
    - Cognitive or learning disabilities.

- WCAG is developed by the W3C (World Wide Web Consortium).

- Four main principles of WCAG
- WCAG follows four important principles, commonly called POUR.
 
1. Perceivable
- Users must be able to perceive the information.
- Example: Add alternative text (alt) to images so screen readers can describe them.

 2. Operable

- Users must be able to operate the website.
- Example: All buttons, links and menus should work using a keyboard without a mouse.

- ACCESSIBLE WEBSITES AND THE PUBLIC SECTOR
 
3. Understandable

- Website content and functionality should be easy to understand.

- Example: Forms should have clear labels and understandable error messages.


 
4. Robust

- Website content should work with different browsers and assistive technologies.
- Example: Use proper HTML elements and semantic tags.

##### Validate form elements

- In HTML, we can validate form elements using HTML5 built-in form validation attributes without writing JavaScript.
- HTML provides attributes like `required`, `minlength`, `maxlength`, `pattern`, `min`, `max`, and `type`.

##### Important HTML validation attributes

| Attribute | Purpose | Example |
| :--- | :--- | :--- |
| `required` | Field must be filled | `required` |
| `minlength` | Minimum characters | `minlength="3"` |
| `maxlength` | Maximum characters | `maxlength="20"` |
| `min` | Minimum numeric value | `min="18"` |
| `max` | Maximum numeric value | `max="60"` |
| `pattern` | Validate using regex | `pattern="[0-9]{10}"` |
| `type="email"` | Validate email format | `type="email"` |
| `type="url"` | Validate URL format | `type="url"` |
| `step` | Allowed numeric increments | `step="2"` |


- `required` checks whether the user entered a value.
- `pattern` checks whether the entered value matches a specified regular expression.
- `type="email"` checks basic email format.