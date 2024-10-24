<div align="center"><h1><a href="https://www.galaxyweblinks.com/" target="_blank">Galaxy Weblinks</a></h1></div>

# FacetWP - Code Snippets

![Licence](https://img.shields.io/badge/Unlicense-red)

## Overview

This is a list of useful **WordPress** and **FacetWP** code snippets and functions that I often reference to enhance or clean up my sites. 

**Note:** Please be careful and make backups!

## FacetWP

- [Hide Count from all facets dropdown UI](#hide-count-from-all-facets-dropdown-ui)
- [Hide Count from specific facets dropdown UI](#hide-count-from-specific-facets-dropdown-ui)

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

---

## License

This repository is unlicense[d], so feel free to fork.
