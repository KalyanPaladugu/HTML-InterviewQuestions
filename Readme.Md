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

- upload and download file
```
<!-- Upload -->
<input type="file" />

<!-- Download -->
<a href="sample.pdf" download>
  Download File
</a>
```
- Upload only images
```
<label>Upload Profile Image:</label>

<input
  type="file"
  accept="image/*"
/>
```

- Upload multiple files
```
<label>Upload Documents:</label>

<input
  type="file"
  multiple
/>
```
- Audio element
```
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```
- Video example:
```
<video width="400" controls>
  <source src="video.mp4" type="video/mp4" />
</video>
```

- Picture Element
- The HTML5 `<picture>` element is used to display responsive images based on screen size, device resolution, or supported image formats.
- It allows the browser to choose the most suitable image from multiple sources.
```
<!DOCTYPE html>
<html>
<body>

  <h2>Responsive Image Example</h2>

  <picture>
    <source
      media="(max-width: 600px)"
      srcset="mobile.jpg"
    />

    <source
      media="(min-width: 601px)"
      srcset="desktop.jpg"
    />

    <img
      src="desktop.jpg"
      alt="Nature Image"
      width="100%"
    />

  </picture>

</body>
</html>
```
How does it work?
- If the screen width is 600px or less, the browser loads mobile.jpg.
- If the screen width is greater than 600px, it loads desktop.jpg.
- The <img> element provides the fallback image.

Example: Different image formats
- We can also provide different image formats.
```
<picture>

  <source
    srcset="nature.avif"
    type="image/avif"
  />

  <source
    srcset="nature.webp"
    type="image/webp"
  />

  <img
    src="nature.jpg"
    alt="Nature"
    width="400"
  />

</picture>
```
> Important: The `<img>` element is mandatory inside `<picture>`. It provides the fallback and accessibility information

##### Web Accessibility (A11Y) and ARIA Roles
- Web accessibility means designing and developing websites so that everyone can use them, including people with disabilities such as visual, hearing, motor, and cognitive impairments.
- A11Y is a short form of Accessibility:
    - A = First letter
    - 11 = Number of letters between A and Y
    - Y = Last letter
- Different users interact with these elements differently.

| User Group | Primary Requirement | Key Implementation Practices |
| :--- | :--- | :--- |
| **Visually Impaired** | Screen readers | Add descriptive alt text to all images, use semantic HTML headings (`H1`–`H6`), and maintain a minimum 4.5:1 color contrast ratio for normal text. |
| **Hearing Impaired** | Captions and transcripts | Provide synchronized closed captions for all videos and full text transcripts for audio-only media. |
| **Motor Disabilities** | Keyboard navigation | Ensure all interactive elements are reachable via the `Tab` key, provide visible focus indicators, and include "skip to main content" links. |
| **Cognitive Disabilities** | Clear labels and simple instructions | Use plain language, label form fields explicitly, provide helpful error messages, and maintain a predictable layout. |

- What is ARIA?
- ARIA stands for Accessible Rich Internet Applications.

- ARIA provides additional information about HTML elements so assistive technologies, such as screen readers, can understand their purpose, state, and relationships.

- ARIA attributes are especially useful when developing custom UI components.

- There are three main categories:
1. Roles – What is this element?
2. Properties – What information or relationship does it have?
3. States – What is its current condition?

Important ARIA roles with examples:
-----------------------------------

A. role="button":
----------------
- Suppose we create a clickable div instead of a normal button.
```
<div role="button" tabindex="0">
  Submit
</div>
```
- role="button" tells screen readers that this element behaves like a button.
- tabindex="0" makes it keyboard-focusable.

B. role="navigation":
---------------------
- Used to identify navigation sections.
```
<nav role="navigation" aria-label="Main navigation">
  <a href="/">Home</a>
  <a href="/about">About</a>
  <a href="/contact">Contact</a>
</nav>
```

- Note: The <nav> element already has an implicit navigation role, so explicitly adding role="navigation" is unnecessary.

C. role="alert":
----------------
- Used to announce important messages to screen readers.
```
<div role="alert">
  Invalid username or password!
</div>
```

- When this message appears dynamically, screen readers generally announce it automatically.

D. role="dialog":
-----------------
- Used for modal dialogs and popup windows.
```
<div
  role="dialog"
  aria-labelledby="dialogTitle"
  aria-modal="true"
>
  <h2 id="dialogTitle">Confirm Delete</h2>

  <p>Are you sure you want to delete this record?</p>

  <button>Yes</button>
  <button>No</button>
</div>
```

- aria-modal="true" communicates that the dialog is modal.
- A complete modal also needs focus management, including moving focus into it and returning focus when it closes.

E. role="checkbox":
------------------

- Used when implementing custom checkbox components.
```
<div
  role="checkbox"
  aria-checked="true"
  tabindex="0"
>
  Accept Terms and Conditions
</div>
```

Here:
- role="checkbox" identifies the element.
- aria-checked="true" indicates that it is checked.
- tabindex="0" allows keyboard focus.
For normal forms, prefer the native checkbox:
```
<input type="checkbox" id="terms" />
<label for="terms">Accept Terms and Conditions</label>
```

##### Important ARIA attributes

- Difference between these three attributes

| Attribute | Purpose | Example |
| :--- | :--- | :--- |
| `aria-label` | Provides accessible name directly | Close button |
| `aria-labelledby` | Gets accessible name from another element | Form heading |
| `aria-describedby` | Provides additional description | Password instructions |

- Important ARIA states and properties

| Attribute | Purpose | Example |
| :--- | :--- | :--- |
| `aria-hidden` | Hides content from accessibility tree | `aria-hidden="true"` |
| `aria-expanded` | Indicates expanded or collapsed state | `aria-expanded="true"` |
| `aria-checked` | Indicates checkbox state | `aria-checked="true"` |
| `aria-disabled` | Indicates disabled state | `aria-disabled="true"` |
| `aria-required` | Indicates required field | `aria-required="true"` |
| `aria-invalid` | Indicates invalid input | `aria-invalid="true"` |
| `aria-live` | Announces dynamic content updates | `aria-live="polite"` |


###### Keyboard accessibility

Accessibility is not only about screen readers. Users should also be able to navigate websites using a keyboard.

- Important keyboard keys:

| Key | Purpose |
| :--- | :--- |
| Tab | Move to next focusable element |
| Shift + Tab | Move to previous focusable element |
| Enter | Activate links and buttons |
| Space | Activate buttons and toggle checkboxes |
| Escape | Close dialogs or menus when supported |
| Arrow keys | Navigate within certain widgets |

- Example: tabindex
```
<button>First Button</button>

<div tabindex="0">
  Keyboard Focusable Div
</div>

<div tabindex="-1">
  Programmatically Focusable Div
</div>
```

There are three important tabindex values:
- tabindex="0" – Element can receive keyboard focus in normal tab order.
- tabindex="-1" – Element can receive programmatic focus but is skipped by normal Tab navigation.
- tabindex="1" or higher – Creates a custom tab order; generally avoid it.

##### What is XSS (Cross-Site Scripting)?
- XSS is a security attack where an attacker injects malicious JavaScript into a website, which executes in another user's browser.
- How to prevent XSS?
1. Avoid rendering untrusted HTML using dangerouslySetInnerHTML in React.
2. Escape or sanitize user-provided HTML.
3. Validate user inputs.
4. Use Content Security Policy (CSP).
5. Avoid unsafe DOM manipulation such as assigning untrusted content to innerHTML.

- There are 3 main types of XSS (Cross-Site Scripting) attacks:
1. Reflected XSS
2. Stored XSS
3. DOM-based XSS

1. Reflected XSS (Non-persistent XSS)
- In Reflected XSS, an attacker injects malicious JavaScript through a URL or request parameter. The vulnerable website immediately returns that input in its response without proper escaping.

Example:

Suppose a website has a search URL:
```
https://example.com/search?name=Kalyan
```

An attacker creates a malicious URL:
```
https://example.com/search?name=<script>alert('XSS')</script>
```

- If the website directly renders the search parameter as HTML, the JavaScript may execute in the victim's browser.

Prevention:
- Escape user input before rendering.
- Avoid unsafe HTML rendering.
- Implement CSP.

2. Stored XSS (Persistent XSS)
- In Stored XSS, an attacker injects malicious JavaScript into a website, and the application stores it in a database.
- Whenever another user visits the affected page, the malicious script may execute.

Example:

- Imagine a social media application where users can post comments.

An attacker submits:
```
<script>
  alert("Your account is hacked!");
</script>
```

- The application stores this comment in the database.

- When other users open the comments section, the script executes if the application renders the content unsafely.

Prevention:
- Sanitize untrusted HTML.
- Escape content before displaying it.
- Validate user input.
- Use CSP.

- DOM-based XSS
- DOM-based XSS happens when JavaScript processes untrusted input and inserts it into the DOM using an unsafe method.

- In this case, the vulnerability is primarily in client-side JavaScript.

Example:

- Unsafe JavaScript:
```
const params = new URLSearchParams(window.location.search);

const name = params.get("name");

document.getElementById("output").innerHTML = name;
```

- An attacker can provide malicious HTML through the URL parameter, which may execute when assigned to innerHTML.

- Prevention:
    - Use textContent instead of innerHTML when displaying plain text.

##### What is CSP (Content Security Policy)?
- CSP stands for Content Security Policy.
- It is a browser security mechanism that helps prevent XSS attacks by controlling which sources are allowed to load scripts, styles, images, and other resources.

- Example CSP header:
```
Content-Security-Policy: default-src 'self'; script-src 'self'; img-src 'self' https://example.com;
```

Explanation:

| Directive | Purpose |
| :--- | :--- |
| `default-src 'self'` | Allow resources from the same origin by default |
| `script-src 'self'` | Allow scripts from the same origin |
| `style-src 'self'` | Allow styles from the same origin |
| `img-src 'self'` | Allow images from the same origin |
| `connect-src 'self'` | Restrict API connections to the same origin |

- For example, if an attacker injects a script from an unauthorized external domain, CSP can block its execution.

- CSP should generally be configured using HTTP response headers

- Can we configure CSP inside React's index.html?
- Yes, HTML supports CSP using a meta tag.

- Inside public/index.html (or the HTML entry file in Vite):
```<head>
  <meta
    http-equiv="Content-Security-Policy"
    content="default-src 'self'; script-src 'self';"
  />
</head>```


- However, HTTP response headers are preferred because meta-based CSP has limitations and cannot support all CSP features, such as `frame-ancestors`.