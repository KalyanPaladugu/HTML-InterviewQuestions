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
+ Difference between `id` and `class`

```
<p id="uniqueParagraph">This has a unique ID</p>
<p class="highlight">This has a reusable class</p>
<p class="highlight">Another element with same class</p>
```
- Difference between `<strong>`  and `<b>` and difference between `<em>` and `<I>`

    + Prefer `<strong>` and `<em>` when the text carries meaningful emphasis. Use `<b>` and `<b>` only for purely visual styling.

- local storage vs sessionStorage

```
<script>
  // Persists even after closing browser
  localStorage.setItem("user", "Alice");

  // Clears when tab is closed
  sessionStorage.setItem("sessionUser", "Bob");
</script>

```
#### XSS atacks

- Cross-Site Scripting (XSS) is a major web security vulnerability that occurs when an attacker trick a website into executing malicious JavaScript code in a user's browser.

- How XSS Works (The Three Main Types)

1. Stored XSS (Persistent)

- This is the most dangerous type. The malicious script is permanently stored on the target server (e.g., in a database, comment section, or visitor log). When another user visits the page, the browser fetches the stored malicious data and executes it.

- Example: An attacker leaves a comment on a blog: 
```
<script>stealCookies()</script>. 
```
- Every user who reads that blog post will now execute that code.

2. Reflected XSS (Non-Persistent)

- The malicious script is part of the request sent to the server (usually inside a URL query parameter) and is immediately "reflected" back in the HTTP response without being saved.
```
Example: An attacker crafts a link: http://example.com/search?q=<script>alert('hacked')</script>. 
```
- They trick a victim into clicking it, and the website reflects the script back onto the screen, triggering it.

3. DOM-based XSS

- Unlike Stored and Reflected XSS, DOM-based XSS happens entirely in the browser (client-side). The server is never involved. It occurs when a website’s client-side JavaScript reads data from an unsafe source (like the URL hash) and unsafely outputs it into the Document Object Model (DOM).


- Example: JavaScript code reads `window.location.hash` and directly injects it into a div using `element.innerHTML`.

##### How to Fix and Prevent XSS

- Preventing XSS requires a defense-in-depth approach. You should never rely on just one defense mechanism.

1. Context-Aware Output Encoding (Escaping)
- Before putting untrusted data onto a webpage, you must convert special characters into safe HTML entities so the browser treats them as text/data, not executable code.

- Convert: `<` to `&lt;`, `>` to `&gt;`, `&` to `&amp;`, `"` to `&quot`;


Modern frameworks: 
- If you are using React or Next.js, this is largely handled for you out of the box (e.g., JSX safely escapes data rendered in `{variables}`). However, you must be extremely cautious with dangerous escape hatches like `dangerouslySetInnerHTML`.

2. Robust Input Validation & Sanitization

- Validation (Allow-listing): Ensure input matches an expected pattern (e.g., a zip code should only be numbers, an email must have an `@` symbol) before accepting it.
 - // ✅ SAFE: Renders literally as "Hello <b>World</b>" on screen. No code executes.
    - `element.textContent = "Hello <b>World</b>";`
- Sanitization (For Rich Text): If you must allow users to input HTML (like a rich-text blog editor), use a trusted library like DOMPurify to strip out any dangerous tags (like `<script>`, `onerror`, or `onload`) while keeping harmless ones like `<b>` or `<i>`.

```
import DOMPurify from 'dompurify';

// Safe to render even if malicious strings are inside rawInput
const cleanHTML = DOMPurify.sanitize(rawInput);
```
3. Implement Content Security Policy (CSP)
- A CSP is an HTTP header you configure on your server that tells the browser exactly which scripts are allowed to execute. Even if an attacker successfully injects a <script> tag, a strict CSP will block it from running.
- A strong basic CSP header looks like:
```
Content-Security-Policy: default-src 'self'; script-src 'self' https://trustedscripts.com;
```
- This forces the browser to only execute scripts originating from your own domain or specified trusted domains, and completely blocks inline scripts (`<script>alert(1)</script>`).

4. Use `HttpOnly` Cookies for Session Tokens
- If your website uses cookies to keep users logged in, always set the HttpOnly flag on those cookies. This instructs the browser that the cookie should never be accessible via JavaScript (document.cookie), effectively neutralizing an attacker's ability to steal session IDs via XSS.

#### WCAG(Web Content Accessibility Guidelines)-2.1&2.2

Step 1: Catch the Quick Wins (Automated Testing)
- Automated tools can instantly catch about 40–50% of your accessibility bugs (like missing tags or bad color contrast). Start by running these:

- Lighthouse / Axe DevTools: Open your browser's developer tools, run an accessibility audit, and it will give you a literal checklist of what to fix in your code.

- WAVE (Web Accessibility Evaluation Tool): A browser extension that overlays visual indicators directly onto your webpage, showing exactly where headings are broken or where form labels are missing.

Step 2: Implement Core Technical Fixes
 
1. Use Semantic HTML (Instead of Generic Divs)
- Assistive technologies like screen readers rely on HTML tags to understand what a page element actually does.
- Stop doing this: `<div class="nav-button" onclick="submit()">Submit</div>`
- Do this instead: `<button onclick="submit()">Submit</button>`
- By using a native `<button>` or `<a>` tag, the browser automatically builds keyboard support, focus states, and screen reader roles for you for free.

2. Ensure Full Keyboard Navigation
- A core requirement of WCAG is that a user must be able to interact with your site using only a keyboard.

- Focus Indicators: Never use CSS to hide the outline of an item when a user tabs onto it (outline: none). If a user can't see which button is currently highlighted, they are digitally trapped.

- Tab Order: Ensure the navigation flows logically from top-to-bottom, left-to-right.

- Skip Links: Add a hidden "Skip to main content" link at the very top of your HTML page. This allows keyboard users to skip past massive navigation headers straight to the main article.

3. Fix Forms and Labels
- Form fields without explicit text labels are completely blank to a blind user.
```
<!-- ❌ BAD: A screen reader just hears "Input field, blank" -->
<input type="text" placeholder="Search...">

<!-- ✅ GOOD: The label is programmatically tied to the input -->
<label for="search-box">Search the site</label>
<input type="text" id="search-box">
```

4. Upgrade Contrast and Media SafelyColor Contrast: 
- Ensure text has a contrast ratio of at least `$4.5:1$` against its background (`$3:1$` for large text). Use tools like Adobe Color or WebAIM Contrast Checker to verify your palette.
- Alt Text: Give every informative image an alt description. If an image is purely decorative (like a background pattern), give it an empty alt attribute (alt="") so screen readers intentionally skip it.

##### ARIA stands for Accessible Rich Internet Applications.
- It is a set of special HTML attributes created by the W3C that you add to your markup to provide extra context to assistive technologies—like screen readers.
- Before diving in, there is an absolute rule in web development: No ARIA is better than Bad ARIA.

- Whenever possible, you should use Semantic HTML tags (like `<button>`, `<nav>`, or `<dialog>`) because they have accessibility built in by default. You should only use ARIA attributes when native HTML cannot do the job—such as when you are building complex, custom UI widgets (like accordions, tab menus, or custom sliders) using generic `<div>` elements.

1. ARIA Roles
- An ARIA role tells a screen reader what an element is or does, especially when generic HTML is used. Think of it as giving an identity to a nameless element.

Example: Making a custom toggle switch
If you style a `<div>` to look like a button or switch, a blind user will hear nothing but "clickable text" or "group". Adding a role fixes this.
```
<!-- ❌ BAD: Screen reader has no idea this functions as a checkbox -->
<div class="custom-checkbox" onclick="toggle()"></div>

<!-- ✅ GOOD: The role announces it properly -->
<div role="checkbox" aria-checked="false" class="custom-checkbox" onclick="toggle()"></div>
```
- Common Categories of Roles
    - Landmark Roles: Help users navigate zones of a page (e.g., role="search", role="banner" for headers, role="main"). Note: Native tags like `<main>` and `<search>` handle this automatically now.

    - Widget Roles: Give functional meaning to standalone UI components (e.g., role="tooltip", role="dialog" for modals, role="tablist").

2. ARIA States & Properties (The Interactive Layer)

A. States (Things that change frequently)
- `aria-expanded="true/false"`: Tells a user if a dropdown or accordion is open or closed.

- `aria-hidden="true/false"`: Tells the screen reader to completely ignore an element (great for hiding decorative background icons).

B. Properties (Characteristics unlikely to change)
`aria-label`: Gives an element an explicit text announcement when there's no visible text on the screen.

`aria-describedby`: Links an element to another element that contains an explanation or error message for it.