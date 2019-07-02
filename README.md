# Tutorial 1: HTML and CSS

This tutorial aims to build a form which uses some of the abilities of
the Google search engine.

## Introduction

You can see the result of the code by clicking on the "Show" button in the
top of the interface.

1. Open the `index.html` file and find out:
    * where is the language of the document declared?
    * where is the encoding of the document declared?
    * what is the role of the `<link>` tag?
    * where the text in the `<title>` tag will be displayed?

## Write content (HTML)
Keep in mind that HTML must convey only "data" and no style information
at all. In this section, your result will be a bit ugly. Don't worry,
we will fix that in the last section!

1. Give your page a "first level header" with a `<h1>` tag, like
  "My Search Engine".
1. Below this header, write a short text in a `<p>` tag explaining
  that the Google search engine accepts parameters in the url.
1. Add a link in the previous text to the following url:
   https://moz.com/blog/the-ultimate-guide-to-the-google-search-parameters
   which gives an exhaustive list of the possible parameters.
1. Use a the `<ul>` and `<li>` tags in order to list the three parameters
  your page will take into account: the query, the number of results per page
  and the language of the result. The result should look similar to:
  ![List example](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1561989063561)

## Write a form
In this section, we setup the form!

1. First, make a search on Google about "H2G2 Marvin". Look at the url in the top
   of your browser, it should be similar to:
   ```
   https://www.google.com/search?client=firefox-b-d&channel=crow&q=H2G2+Marvin
   ```
   After the question mark `?`, you can see the parameters separated
   with a `&`. You can forget about almost all the parameters except the
   `q=...` which is what we have entered. Note that the space in our request
   has been replaced by a `+` symbol.
   * Modify the URL by hand to search about "H2G2 Ford Perfect"
   * Add the parameter `num=2`. It will display two results per page.
   * Add the parameter `hl=en`. It should display the results in English.
   Change `en` into `fr` (for French) or `it` (for Italian).
1. In `index.html`, add a `<form>` tag with the attribute
  `action="https://www.google.com/search"` in `index.html`. This will make all
  the submissions to the form create a new request to the Google search engine.
1. Add an `<input>` tag of type "text" and name "q" ("type" and "name" are
  attributes of the `input` tag).
1. Add an `<input>` tage of type "submit" and customize the displayed text
   with the attribute "value".
1. Try your form! Enter a string in the field and press "Enter". This should
  redirect you to a Google search. Note that the "q" parameter has been added
  to the url!
1. Proceed in a similar manner to add a field defining the number of results by pages (use the type "number"
  and the attribute "min" to restrict the possible values typed by the user ).
1. Add a label and a "placeholder" on each of this field in order to have a useable form.
  [Click here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Label) for details about labels.
1. Use [radio buttons](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input/radio)
  to let the user choose among French, English or Italian. (the linked document abour radio button
  use `div`s to *list* all the options... What tags would be more appropriate for this purpose?)

## Give it some style!

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <link rel="stylesheet" href="/style.css">
  </head>
  <body>
    <h1 class="page-title">
      My Search Engine
    </h1>

    <div id="description">
      <p>
        The Google search engine allows you to define some paramters in the URL! Here
        are the paramters this forms takes into account:
      </p>
      <ul class="nice-list">
        <li>the query,</li>
        <li>the number of results per page,</li>
        <li>the language of the result.</li>
      </ul>
    </div>
    <form id="search-form" action="https://www.google.com/search">
      <label>Enter your query: <input type="text" name="q" /></label>
      <label>How many results by page?<input type="number" min="0" name="num"/></label>
      <div>
        What language do you want?
        <ul class="nice-list">
          <li><label><input type="radio" name="hl" value="fr" />French</label></li>
          <li><label><input type="radio" name="hl" value="en" />English</label></li>
          <li><label><input type="radio" name="hl" value="it" />Italian</label></li>
        </ul>
      </div>
      <input type="submit" value="Search!"/>
    </form>
  </body>
</html>

```

The challenge of this last part is to use the HTML code above, without editing it.
You only can edit the CSS file to achieve render the HTML like (a field is selected on the second image):

![nice form](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562053335457)



1. Remind you CAN NOT CHANGE THE HTML! To deal with layout, it is recommended
   to use the "flexbox" (or "grid"). For instance, you can apply the rule
   `display: flexbox;` on the `body` tag. Look at the `flex-direction` and `align-items`
   to get:
   ![centered](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562053371475)
   (the font is "Helvetica")
1. Use the id to select the form and play with `display`, `flex-direction`,
   `border`, `border-radius` and `padding` to have:
   ![form 1](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562053410060)
   Make also the form at least 350px wide.
1. Make the tag with id description at most 450px wide and remove the bullets
   of the "nice-list"s (use the `list-style-type` property). Set also the
   margins to 0 for the `p` and `ul` tags.
   You should have something like:
   ![nice list 1](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562053501714)
1. Make the "nice list"s really "nice":
  ![nice list 2](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562053944535)
  The red rule is a 3px wide red border.
  You may need the "child selector" `>` in your selector...
1. Select the submit button in the search form with the selector
   `#search-form input[type=submit]` and play with
   `background-color`,
  `border`,
  `border-radius`,
  `padding`,
  `font-size` and `color` to get:
  ![fat search button](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562054420991)
  (the background color of the button is `#ffa7a7`)
1. Using similar selectors and
`display`,
  `padding`,
  `border-radius`,
  `border`, make the two fields looks like:
  ![nice fields](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562054625181)
1. Using the `:focus` pseudo selector,  make the border "sharper" when on of the
   field is selected:
   ![field selected](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562055138123)
   (the border color is pure "red")
1. Set a vertical margin of 20px on each of the immediate child of the form (it is only
   one selector and one property):
   ![form spaced](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562055298955)
   By the way, using space to isolate content is often prettier than draw
   rules.
1. Using the `:before` pseudo selector and the `content` property, add the text
   "My form" in red on the top of your form. Color the title in red... Tada:
   ![complete](https://cdn.glitch.com/0f90b5e2-6644-4dc1-9d49-3369ad8943b1%2Fimage.png?v=1562055465914)




