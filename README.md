<div align="center"><h1><a href="https://www.galaxyweblinks.com/" target="_blank">Galaxy Weblinks</a></h1></div>

# FacetWP - Code Snippets

![Licence](https://img.shields.io/badge/Unlicense-red)

## Overview

This is a list of useful **WordPress** and **FacetWP** code snippets and functions that I often reference to enhance or clean up my sites. 

**Note:** Please be careful and make backups!

## FacetWP

- [Hide Count from all facets dropdown UI](#hide-count-from-all-facets-dropdown-ui)
- [Hide Count from specific facets dropdown UI](#hide-count-from-specific-facets-dropdown-ui)
- [Add a CSS class to the Sort facet’s "select" element](#add-a-css-class-to-the-sort-facets-select-element)

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
 * If you want to hide counts from specific facets with a dropdown UI, then use this, add the following to your theme’s functions.php:
 */

// With JS:
add_action( 'facetwp_scripts', function() {
```
    <script>
      document.addEventListener('facetwp-loaded', function() {
        fUtil('.facetwp-type-sort select').addClass('form-select');
      });
    </script>
```php
}, 100 );

// Or, with PHP:
add_filter( 'facetwp_facet_html', function( $output, $params ) {
  if ( 'sort' == $params['facet']['type'] ) { //
    $output = str_replace( 'select', 'select class="form-select"', $output );
  }
  return $output;
}, 10, 2 );

```

---

## License

This repository is unlicense[d], so feel free to fork.
