---
$title: Style & layout
$order: 0
toc: true
components:
    - youtube
---
[TOC]

Styling and layout on AMP HTML pages is very similar to normal HTML pages – in
both cases, you'll use CSS.

However, AMP limits some use of CSS for performance and usability reasons, while
expanding responsive design capabilities with features like [placeholders & fallbacks]({{g.doc('/content/docs/design/responsive_amp/placeholders.md', locale=doc.locale).url.path}}),
[advanced art direction via srcset]({{g.doc('/content/docs/design/responsive_amp/art_direction.md', locale=doc.locale).url.path}}) and the [layout attribute]({{g.doc('/content/docs/design/responsive_amp/control_layout.md', locale=doc.locale).url.path}}) for better control over how your elements display.

Tip: It is super easy to make elements responsive in AMP. Just put `layout="responsive"` on them. To learn more about Responsive Design in AMP, head to [Create Responsive AMP Pages](/docs/design/responsive/responsive_design.html).

{{ youtube('y6kA3u3GIws', 480, 270, caption='Watch UpperQuad talk about the AMPproject site redesign, including the challenges of using AMP for the first time.') }}

## Add styles to a page

Add your CSS inside a `<style amp-custom>` tag in the head of the document.
For example:

[sourcecode:html]
<!doctype html>
  <head>
    ...
    <style amp-custom>
      /* any custom styles go here. */
      body {
        background-color: white;
      }
      amp-img {
        border: 5px solid black;
      }

      amp-img.grey-placeholder {
        background-color: grey;
      }
    </style>
    ...
  </head>
[/sourcecode]

Important: Make sure there’s only one `<style amp-custom>` tag on your page, as more than one isn’t allowed in AMP.

Define component styles with class or element selectors
using common CSS properties. For example:

[sourcecode:html]
<body>
  <p>Hello, Kitty.</p>
  <amp-img
    class="grey-placeholder"
    src="https://placekitten.com/g/500/300"
    srcset="/img/cat.jpg 640w,
           /img/kitten.jpg 320w"
    width="500"
    height="300"
    layout="responsive">
  </amp-img>
</body>
[/sourcecode]

Important: Check that your styles are supported in AMP; some styles aren't for performance reasons (see also [Supported CSS]({{g.doc('/content/docs/design/responsive_amp/style_pages.md', locale=doc.locale).url.path}})).

If needed, AMP also allows inline styles. For example:

[sourcecode:html]
<body>
  <p style="color:pink;margin-left:30px;">Hello, Kitty.</p>
</body>
[/sourcecode]

## Layout elements responsively

Specify the size and position for all visible AMP elements
by providing a `width` and `height` attribute.
These attributes imply the aspect ratio of the element,
which can then scale with the container.

Set the layout to responsive.
This sizes the element to the width of its container element
and resizes its height automatically to the aspect ratio given by width and height attributes.

Read on: Learn more about [supported layouts in AMP]({{g.doc('/content/docs/design/responsive_amp/control_layout.md', locale=doc.locale).url.path}})

## Provide placeholders & fallbacks

The built-in support for placeholders and fallbacks means your users never have to stare at a blank screen again.

Read on: Learn more about [Placeholders and fallbacks]({{g.doc('/content/docs/design/responsive_amp/placeholders.md', locale=doc.locale).url.path}})

## Art direct your images

AMP supports both `srcset` and `sizes` attributes to give you fine grained control, of which images to load in which scenario.

Read on: Learn more about [art direction with srcset and sizes]({{g.doc('/content/docs/design/responsive_amp/art_direction.md', locale=doc.locale).url.path}})

## Validate your styles and layout

Use the AMP validator to test
your page's CSS and layout values.

The validator confirms that your page’s CSS doesn’t exceed 50,000 bytes limit,
checks for disallowed styles, and ensures that the page's layout
is supported and correctly formatted.
See also this complete list of [Style and layout errors](/docs/troubleshooting/validation_errors.html#style-and-layout-errors).

Example error in console for page with CSS that exceeds the 50,000 bytes limit:

<amp-img src="/static/img/docs/too_much_css.png" width="1404" height="334" layout="responsive"></amp-img>

Read on: Learn more about how to [validate and fix your AMP pages]({{g.doc('/content/docs/fundamentals/validate.md', locale=doc.locale).url.path}})
