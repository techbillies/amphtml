<!---
Copyright 2016 The AMP HTML Authors. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# <a name="amp-sidebar"></a> `amp-sidebar`

<table>
  <tr>
    <td width="40%"><strong>Description</strong></td>
    <td>A sidebar provides a way to display meta content intended for temporary access (navigation links, buttons, menus, etc.).The sidebar can be revealed by a button tap while the main content remains visually underneath.</td>
  </tr>
  <tr>
    <td width="40%"><strong>Availability</strong></td>
    <td><div><a href="https://www.ampproject.org/docs/reference/experimental.html">Experimental</a>; no validations yet.</div><div>Work in progress.</div></td>
  </tr>
  <tr>
    <td width="40%"><strong>Required Script</strong></td>
    <td><code>&lt;script async custom-element="amp-sidebar" src="https://cdn.ampproject.org/v0/amp-sidebar-0.1.js">&lt;/script></code></td>
  </tr>
  <tr>
    <td width="40%"><strong>Examples</strong></td>
    <td>None</td>
  </tr>
</table>

## Behavior

- There can be only one `<amp-sidebar>` in an AMP document. The `<amp-sidebar>` should be a direct child of the `<body>`.
- The sidebar can only appear on the left or right side of a page.
- The `<amp-sidebar>` may contain any valid HTML elements (supported by AMP).
- The `<amp-sidebar>` may not contain any AMP Elements except for `amp-accordion`, `amp-img` and `amp-fit-text`.
- The max-height of the sidebar is 100vh, if the height exceeds 100vh then a vertical scrollbar appears. The default height is set to 100vw in CSS and is overridable in CSS.
- The width of the sidebar can be set and adjusted between 45px and 80vw using CSS.
- Touch zoom is disabled on the `amp-sidebar` and it's mask when the sidebar is open.

Example:
```html
<amp-sidebar id='sidebar1' layout='nodisplay'>
  <ul>
    <li> Nav item 1</li>
    <li> Nav item 2</li>
    <li> Nav item 3</li>
    <li> Nav item 4</li>
    <li> Nav item 5</li>
    <li> Nav item 6</li>
    <li> Nav item 7</li>
    <li> Nav item 8</li>
    <li> Nav item 9</li>
    <li on="tap:sidebar1.close"> Close</li>
  </ul>
</amp-sidebar>
```

### Opening and Closing the Sidebar
Setting the `on` attribute on one or more elements within the page and setting it's method to `toggle` will toggle the sidebar when the element is tapped or clicked. Setting the element's method to `open` or `close` will open or close the sidebar.Tapping back on the partially-visible main content area closes the sidebar.

Alternatively pressing the escape key on the keyboard will also close the lightbox.

Example:
```html
<div class="hamburger" on='tap:sidebar1.toggle'></button>
<button on='tap:sidebar1'>Open</button>
<button on='tap:sidebar1.open'>Open</button>
<button on='tap:sidebar1.close'>x</button>
```

## Attributes

**side**

The `side` attribute may be set to `left` or `right` depending upon whether sidebar should open in the left or right side of the page. If a `side` is not set on the `amp-sidebar` then it will be inherited from the `body` tag's `dir` attribute (`ltr` => `left` , `rtl` => right') and if one does not exist then the `side` is defaulted to `left`.

**open**

The `open` attribute is present on the sidebar when it is open.

**layout**

The only permissible value for the `layout` attribute in `amp-sidebar` is `nodisplay`.

## Styling

The `amp-sidebar` component can be styled with standard CSS.

- The `width` of the `amp-sidebar` may be set to adjust the width of the sidebar between the pre-set min(45px) and max(80vw) values.
- The height of the `amp-sidebar` may be set to adjust the height of the sidebar if required. If the height exceeds 100vw then the sidebar will have a vertical scrollbar. The preset height of the sidebar is 100vw and can be overridden in CSS to make it shorter.
- The current state of the sidebar is exposed via the `open` attribute that is set on the `amp-sidebar` tag when the side bar is open on the page.

## Validation errors

The following lists validation errors specific to the `amp-sidebar` tag
(see also `amp-sidebar` in the [AMP validator specification](https://github.com/ampproject/amphtml/blob/master/extensions/amp-sidebar/0.1/validator-amp-sidebar.protoascii)):

<table>
  <tr>
    <th class="col-fourty"><strong>Validation Error</strong></th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="col-fourty"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#tag-required-by-another-tag-is-missing">The 'example1' tag is missing or incorrect, but required by 'example2'.</a></td>
    <td>Error thrown when required <code>amp-sidebar</code> extension <code>.js</code> script tag is missing or incorrect.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#disallowed-tag-ancestor">The 'example1' may not appear as a descendant of tag 'example2'.</a></td>
    <td>Error thrown when <code>amp-sidebar</code> is a child of <code>amp-sidebar</code>.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#invalid-attribute-value">The attribute 'example1' in tag 'example2' is set to the invalid value 'example3'.</a></td>
    <td>Error thrown when the <code>side</code> attribute is invalid.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#implied-layout-isnt-supported-by-amp-tag">The implied layout 'example1' is not supported by tag 'example2'.</a></td>
    <td>The only supported layout type is <code>NODISPLAY</code>. Error thrown if implied layout is any other value.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#specified-layout-isnt-supported-by-amp-tag">The specified layout 'example1' is not supported by tag 'example2'.</a></td>
    <td>The only supported layout type is <code>NODISPLAY</code>. Error thrown if specified layout is any other value.</td>
  </tr>
</table>
