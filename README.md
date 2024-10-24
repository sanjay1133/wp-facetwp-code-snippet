<div align="center"><h1><a href="https://www.galaxyweblinks.com/" target="_blank">Galaxy Weblinks</a></h1></div>

# FacetWP - Code Snippets

![Licence](https://img.shields.io/badge/Unlicense-red)

## Overview

This repository contains a collection of code snippets and functions that can be used to enhance or streamline your **WordPress** and **FacetWP** projects. 

**Note:** Please be careful and make backups!

## FacetWP

- [Hide Count from all facets dropdown UI](#hide-count-from-all-facets-dropdown-ui)
- [Hide Count from specific facets dropdown UI](#hide-count-from-specific-facets-dropdown-ui)
- [Add a CSS class to the Sort facet's "select" element](#add-a-css-class-to-the-sort-facets-select-element)
- [Disable parents with children in fselect](#disable-parents-with-children-in-fselect)
- [Add label or aria-label to fSelect facets search input field](#Add-label-or-aria-label-to-fSelect-facets-search-input-field)

---

## FacetWP

### Hide Count from all facets dropdown UI

```php
/**
 * To hide counts from all facets of a type that use a dropdown UI (all Dropdown facets, fSelect facets, Hierarchy Select facets, and Range List facets (in dropdown or fSelect UI mode)), add the following to your theme’s functions.php:
 */

add_filter( 'facetwp_facet_dropdown_show_counts', '__return_false' );

```

### Hide Count from specific facets dropdown UI

```php
/**
 * If you want to hide counts from specific facets with a dropdown UI, then use this, add the following to your theme’s functions.php:
 */

add_filter( 'facetwp_facet_dropdown_show_counts', function( $return, $params ) {
  if ( 'your_facet_name' == $params['facet']['name'] ) {
    $return = false;
  }
  return $return;
}, 10, 2 );

```

### Add a CSS class to the Sort facet’s "select" element

```php
/**
 * Add a CSS class to the Sort facet’s "select" element
 */

// With JS:
add_action( 'facetwp_scripts', function() {
?>
    <script>
      document.addEventListener('facetwp-loaded', function() {
        fUtil('.facetwp-type-sort select').addClass('form-select');
      });
    </script>
<?php
}, 100 );
// Or, with PHP:
add_filter( 'facetwp_facet_html', function( $output, $params ) {
  if ( 'sort' == $params['facet']['type'] ) { //
    $output = str_replace( 'select', 'select class="form-select"', $output );
  }
  return $output;
}, 10, 2 );
```

### Add label or aria-label to fSelect facets search input field

```php
/**
 * Add label or aria-label to fSelect facets search input field
 */
add_action('facetwp_scripts', function () {
?>
    <script>
        FWP.hooks.addAction('facetwp/loaded', function() {

            /** adds aria-label to input */
            fUtil('.facetwp-type-fselect .fs-search input').each(function() {
                fUtil(this).attr('aria-label', 'this is the label');
            });

            /** prepends <label> and text to input  */

            // element that will be wrapped
            var el = document.querySelector('.facetwp-type-fselect .fs-search input');

            // create wrapper container
            var wrapper = document.createElement('label');

            // insert wrapper before el in the DOM tree
            el.parentNode.insertBefore(wrapper, el);

            // add label text
            wrapper.textContent = "This is the label";

        }, 1000);
    </script>
<?php
}, 100);
```

---

## License

This repository is unlicense[d], so feel free to fork.
