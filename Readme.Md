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
+ We can achieve this by using element **<a>** and the attribute **download**
```html
<a href="file_name_to_download.pdf" download>  Download the file </a>
```

