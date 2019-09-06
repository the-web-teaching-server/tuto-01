# Tutorial 1: HTML and CSS

This tutorial aims at helping you build a form which uses some of the abilities of
the Google search engine.

## Introduction

You can see the result of the code by clicking on the "Show" button at the
top of the interface.

1. Open the `index.html` file and find out:
    * where the language of the document declared is,
    * where the encoding of the document declared is,
    * what the role of the `<link>` tag is,
    * where the text in the `<title>` tag will be displayed.

## Write content (HTML)
Keep in mind that HTML must only convey "data" and no style information
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
  ![List example](https://cdn.glitch.com/da30473a-a784-4c61-bf9a-f183a47427d2%2Fimage.png?v=1567514009702)

## Write a form
In this section, we setup the form!

1. First, make a search on Google about "H2G2 Marvin". Look at the url at
   the top
   of your browser, it should be similar to:
   ```
   https://www.google.com/search?client=firefox-b-d&channel=crow&q=H2G2+Marvin
   ```
   After the question mark `?`, you can see the parameters separated
   with a `&`. You can ignore almost all parameters except the
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
1. Add an `<input>` tag of type "submit" and customize the displayed text
   with the attribute "value".
1. Try your form! Enter a string in the field and press "Enter". This should
  redirect you to a Google search. Note that the "q" parameter has been added
  to the url!
1. Proceed in a similar manner to add a field defining the number of results by pages.

  *Note: you can use the type "number"
  and the attribute "min" to restrict the possible values typed by the user. Do
  not forget to specify the `name` attribute!
1. Add a label and a "placeholder" in both fields in order to have a useable form.
  [Click here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Label) for details about labels.
1. Use [radio buttons](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input/radio)
  to let the user choose among French, English or Italian. (the linked document about radio button
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
        The Google search engine allows you to define some parameters in the URL! Here
        are the paramters this forms takes into account:
      </p>
      <ul class="nice-list">
        <li>the query,</li>
        <li>the number of results per page,</li>
        <li>the language of the result,  which can be either:
          <ul>
            <li>French</li>
            <li>English</li>
            <li>Italian</li>
          </ul>
        </li>
      </ul>
    </div>
    <form id="search-form" action="https://www.google.com/search">
      <label>Enter your query: <input type="text" name="q" /></label>
      <label>How many results per page?<input type="number" min="0" name="num"/></label>
      <div>
        Choose your search language:
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
You only can edit the CSS file to render the HTML like (the steps will be
detailled below, keep reading!):

![nice form](/imgs/complete.png)


1. Remind you HAVE to use the above HTML code and you CANNOT CHANGE IT! To deal
   with layout, it is recommended
   to use the "flexbox" layout. For instance, you can apply the rule
   `display: flex;` on the `body` tag. Look at the `flex-direction` and `align-items`
   to get:

   ![centered](/imgs/step1.png)

   (the font is "Helvetica")
1. Use the id to select the form and play with `display`, `flex-direction`,
   `border`, `border-radius` and `padding` to have:

   ![form 1](/imgs/step2.png)

   Make also the form at least 350px wide.
1. Make the tag with id description at most 450px wide and remove the bullets
   of the "nice-list"s (use the `list-style-type` property). Set also the
   margins to 0 for the `p` and `ul` tags.
   You should have something like:

   ![nice list 1](/imgs/step3.png)

   *Note:* you may need to add some margin and/or padding to the `li` tags.
1. Make the "nice list"s really "nice" (you only need `border-left` and
   some `padding` and `margin`):

   ![nice list 2](/imgs/step4.png)

   The red rule is a 3px wide red border.
   You may need the "child selector" `>` in your selector...
1. Select the submit button in the search form with the selector
   `#search-form input[type=submit]` and play with
   `background-color`,
   `border`,
   `border-radius`,
   `padding`,
   `font-size` and `color` to get:

   ![fat search button](/imgs/step5.png)

   (the background color of the button is `#ffa7a7`)
1. Using similar selectors and
   `display`,
   `padding`,
   `border-radius`,
   `border`, make the two fields looks like (the border color
   of the fields is `#ffa7a7`):

   ![nice fields](/imgs/step6.png)

1. Using the `:focus` pseudo selector,  make the border "sharper" when on of the
   field is selected:
   ![field selected](/imgs/step7.png)

   (the border color is pure "red")
1. Set a vertical margin of 20px on each of the immediate child of the form (it is only
   one selector and one property; `*` selector can be useful):

   ![form spaced](/imgs/step8.png)

   By the way, using space to isolate content is often prettier than draw
   rules.
1. Using the `:before` pseudo selector and the `content` property, add the text
   "My form" in red on the top of your form. Color the title in red... Tada:

   ![complete](/imgs/complete.png)
