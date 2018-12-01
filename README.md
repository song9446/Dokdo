# Dokdo
`Dokdo` is static html template compiler written in pure Python. It is inspired by [Vue.js][vue.js].

# Why another template engine?
- Server-side template engines require particular server framework
- Client-side template engines require particular client framework
- Most of template engines focus on dynamic templating(means less static features and have overhead)
- I wanted to avoid HTML code redundancy and I don't wanted to hang on particular framework
- So I made it myself

# Who should use this framework
- Who needs powerful static html template compiler
- Who totally seperates dynamic part and static part on their project
- Who only deals with HTML(you don't have to know other programming language)

# Who should NOT use this framework
- Who need dynamic templating
- Who already decided to use particular web framework FOREVER(most of them provide templating feature)

# Usage
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
  {{{ text }}}
</span>
```

`$ ./Dokdo.py -c index.html -o out.html`

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

