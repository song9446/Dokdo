# Dokdo
`Dokdo` is static HTML template compiler written in pure Python. It is inspired by [Vue.js][vue.js].

## Philasophy
NO server, NO client, NO other programming language. ONLY HTML.

It has similar grammar with HTML tag for consistency. You can thought it as an extension of HTML.

## Why another template engine?
- Server-side template engines require a particular server framework
- Client-side template engines require a particular client framework
- Most of template engines focus on dynamic templating(means less static features and have overhead)
- I wanted to avoid HTML code redundancy and I didn't want to hang on a particular framework
- So I made it myself

## Who should use this template compiler
- Who needs powerful static html template compiler
- Who completely separates a dynamic part from a static part in their project
- Who only deals with HTML(you don't have to know other programming languages)
- Who wants to avoid HTML code redundancy without hanging on a particular framework

## Who should NOT use this template compiler
- Who needs dynamic templating
- Who already decided to use particular web framework FOREVER(most of them provide templating feature)

## Usage
index.html
```html
<import path="templates/cap.tmpl" title="title variable">
  <div> 
    This is index page 
    <import path="components/fancy-text.comp">
      this is so fancy!
    </import>
  </div>
</import>
```
templates/cap.tmpl
```html
<!DOCTYPE html>
<html>
  <head>
    <title> {{{ title }}} </title>
  </head>
  <body>
    <header>cap</header>
    <innerhtml> cap this contents! </innerhtml>
    <footer>cap</footer>
  </body>
</html>
```
components/fancy-text.comp
```html
<style type="text/scss">   
  .fancy-text {
    color: #f00;
    background-color: #0f0;
  }
</style>
<span class="fancy-text">
  <innerhtml></innerhtml>
</span>
```

`$ ./dokdo.py -c index.html -o out.html`

out.html
```html
<!DOCTYPE html>
<html>
  <head>
    <title> title variable </title>
    <style>
      .fancy-text {
         color: #f00;
         background-color: #0f0;
      }
    </style>
  </head>
  <body>
    <header>cap</header>
    <div> 
      This is index page 
      <span class="fancy-text">
        this is so fancy!
      </span>
    </div>
    <footer>cap</footer>
  </body>
</html>
```
# Dependency
python3 lxml, libsass


[vue.js]: https://github.com/vuejs/vue

