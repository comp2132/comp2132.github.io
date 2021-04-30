* TOC
{:toc}



# COMP 2132 - Web Development with Javascript



## Assignment/Quiz Schedule

| Date | Items |
| --- | --- |
| Lesson 2 | Quiz 1, Assignment 1 due |
| Lesson 3 | Quiz 2, Assignment 2 due 
| Lesson 4 | Quiz 3 |
| Lesson 5 | Quiz 4, Assignment 3 due |
| Lesson 6 | Quiz 5, Final Project assigned |
| Lesson 7 | Quiz 6, Assignment 4 due |
| Lesson 8 | Quiz 7 |
| Lesson 9 | Quiz 8, Assignment 5 due |
| Lesson 10 | Quiz 9, Assignment 6 due |
| Lesson 11 | Quiz 10 |
| Lesson 12 | Final Exam, Final Project due |



## Grades

Grades will be available on the Learning Hub, final marks are posted on [https://my.bcit.ca](https://my.bcit.ca)

### Assignments

| Assignment | Weight (% of final grade) |
| --- | --- |
| Assignment 1 | 2% |
| Assignment 2 | 3% |
| Assignment 3 | 5% |
| Assignment 4 | 5% |
| Assignment 5 | 5% |
| Assignment 6 | 5% |
| Total | 25% |

### Final Project

| --- | --- |
| Final Project | 25% |

### Quizzes

| Quiz | Weight (% of final grade) |
| --- | --- |
| Quiz 1 | 1% |
| Quiz 2 | 1% |
| Quiz 3 | 2% |
| Quiz 4 | 3% |
| Quiz 5 | 3% |
| Quiz 6 | 3% |
| Quiz 7 | 3% |
| Quiz 8 | 3% |
| Quiz 9 | 3% |
| Quiz 10 | 3% |
| Total | 25% |

### Final Exam

| --- | --- |
| Final Exam | 25% |



## Submitting Homework

Homework will be submitted to the Learning Hub unless otherwise specified



## Introducing JavaScript

- JavaScript was invented by Netscape in 1995
- JavaScript was the first client-side scripting language
- JavaScript runs in the browser, on the server, 
- ECMAScript is the standardized version of JavaScript

### What JavaScript Can Do

- Dynamically create HTML/CSS
- Update HTML/CSS without reloading the page
- Timers and event handling
– and much more...

### What JavaScript __Cannot__ Do

- Read (or write to) the client’s file system
- Send emails without the client’s knowledge/consent
- Close browser windows it did not open
- Execute programs on the client’s computer
- Open tiny windows (less than 100px x 100px)
- Read the browser’s history (links, yes; read, no)



## Useful Sites/Resources

Mozilla Developer Network – <https://developer.mozilla.org/en-US/docs/Web/JavaScript>

ECMA Standards – <http://www.ecmascript.org>

JavaScript Lint Tool – <http://www.jshint.com>

Online Help – <http://stackoverflow.com>

Atom Editor – <https://atom.io>

Emmet – <https://emmet.io>



## Our First Scripts

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <script>
        alert('Hello World');
    </script>
</body>
</html>
```

In between the `<script>` and `</script>` tags, only JavaScript can appear. Do not put HTML.\


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <script>
        <h1> Error! </h1>
    </script>
</body>
</html>
```


## Where To Write JavaScript

We can write JavaScript in the `<head>` section, or the `<body>` section, or in an external file, loaded with a `<script>` tag.

### Problem

Although the head section is often a great place to put JavaScript code, one browser behaviour needs to be considered first.

The browser loads a page from top to bottom, and the `<head>` section gets loaded before any of the `<body>` section gets rendered. Because of this, JavaScript running in the `<head>` may not be able to target elements in the body.\


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script>
        document.getElementById('myH1');  
        /* 
          ERROR! Because the head is loaded before
          the body, the h1 tag has not been created yet,
          so the JavaScript interpreter thinks the element
          does not exist
        */
    </script>
</head>
<body>
    <h1 id="myH1">My Heading</h1>
</body>
</html>
```

### Solution

We can move the script _after_ the h1 tag, or we can _delay_ the script in the head using `window.onload`

Moving the script after the tag:\


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <h1 id="myH1">My Heading</h1>
    <script>
        document.getElementById('myH1'); // Works!
    </script>
</body>
</html>
```

Using `window.onload`:\

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script>
        window.onload = function() {
            document.getElementById('myH1'); // Works!
        }
    </script>
</head>
<body>
    <h1 id="myH1">My Heading</h1>
</body>
</html>
```

### External Scripts

We can also put our JavaScript into an external file. __Note__: you can only load external scripts by using the _src_ attribute with a filename and path.\


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script src="myJSfile.js"></script>
</head>
<body>
    <h1 id="myH1">My Heading</h1>
</body>
</html>
```

Similarly, external JavaScript files can be delayed using the _defer_ attribute. Deferred scripts will begin downloading right away, but will not execute until the entire document is rendered. After the page is finished, all deferred external JavaScript files will execute in the same order in which they were declared.\


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script src="myJSfile.js" defer></script>
            <!--  OR  -->
    <script src="myJSfile.js" defer='defer'></script>
</head>
<body>
    <h1 id="myH1">My Heading</h1>
</body>
</html>
```



## Comments

Comments are “notes” that are ignored by JavaScript and are intended for humans to read instead.

There are two types of comment tags used in JavaScript:  
1.  // comments out everything until the end of the line  
2. `/*` comments out everything until `*/` is found. This can span multiple lines  