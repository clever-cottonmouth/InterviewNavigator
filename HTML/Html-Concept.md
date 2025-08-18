What are semantic and non-symentic HTML elements ?

Semantic elements: They clearly describes what type of content they hold.
Eg: header,article,nav,footer,section etc.

Non-semantic elements: They acts as placeholders but does not describe what type of content they hold.
Eg: div,span etc.

---

In one of my frontend machine coding interviews, i was asked to resolve below issue in hashtag#css ? Add your comments on how you will resolve this issue

play with logic in this fiddle: https://jsfiddle.net/gzfjyh45/16/

1. Modify the css code such that child blocks should not overflow the parent container (All child blocks should be in square shape after css modifications and they should be with in container)?
2. Modify the css to display all 3 blocks in diagonal to container.

NOTE: Should not change existing width, height & border.

Below is the logic that you need to modify.

<div class="container">
 <div class="block">1</div>
 <div class="block">2</div>
 <div class="block">3</div>
</div>

.container {
 border: 1px solid black;
 height: 180px;
 width: 180px;
}

.block {
 border: 1px solid gray;
 height: 60px;
 width: 60px;
}

---

What is viewport ?

It is the area of the webpage in which the content is visible to the user.
viewport size varies based on the screen size.

<meta name="viewport" content="width=device-width, initial-scale=1.0">
__________________________________________________________________________________________________________________________________________________________________________________________________________________
 What is meta in html ?

meta tags are placed inside the head section of html document and will provide all the information about the html document which includes page title, description, author, charset etc.

It contains below attributes.,
name,content,charset,http-equiv.

# target="_blank" vs. target="_new"


## Difference between link tag `<link>` and anchor tag `<a>`?

The anchor tag `<a>` is used to create a hyperlink to another webpage or to a certain part of the webpage and these links are clickable, whereas, link tag `<link>` defines a link between a document and an external resource and these are not clickable.

## What is new about the relationship between the `<header>` and `<h1>` tags in HTML5?

As HTML5 was all about better semantics and arrangements of the tags and elements, the `<header>` tag specifies the header section of the webpage. Unlike in previous version there was one `<h1>` element for the entire webpage, now this is the header for one section such as `<article>` or `<section>`. According to the HTML5 specification, each `<header>` element must at least have one `<h1>` tag

### What is the difference between `<figure>` tag and `<img>` tag?

### Is the `<datalist>` tag and `<select>` tag same?

### What are Semantic Elements?

Semantic elements are those which describe the particular meaning to the browser and the developer. Elements like `<form>`, `<table>`, `<article>`, `<figure>`, etc., are semantic elements

### Is drag and drop possible using HTML5 and how?

Yes, in HTML5 we can drag and drop an element. This can be achieved using the drag and drop-related events to be used with the element which we want to drag and drop.

### What type of audio files can be played using HTML5?

HTML5 supports the following three types of audio file formats:

1. Mp3
2. WAV
3. Ogg

### What is the usage of a novalidate attribute for the form tag that is introduced in HTML5?

### What is a manifest file in HTML5?

### What is the Geolocation API in HTML5?

## What do *DOCTYPE* and *html lang* attributes do?

## Can you explain the purpose of *meta tags* in HTML?

## What is the difference between *b* and *strong* tags?

## When would you use *em* over  *i* , and vice versa?

### **What is the use of an iframe tag?**

## What is the purpose of  *small* ,  *s* , and *mark* tags?

### **What is the purpose of the data-* attribute in HTML? Provide an example use case.**

### **What is the difference between the defer and async attributes in the `<script>` tag? **

### **What are void tags in HTML5?**

### MathML

## WebWorker

## Not Valid tag in html5

---
