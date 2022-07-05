# WordPress & PHP Cheatsheet

## Prevent files from being called directly

```bash
if( ! defined(  'ABSPATH' ) ) { exit; }
```

## Sanitizing

### Sanitizing inputs in WordPress

https://developer.wordpress.org/themes/theme-security/data-sanitization-escaping 

### Sanitizing and validating in PHP

https://www.w3schools.com/php/php_filter.asp

### Preventing injections

`htmlentities()` saves from HTML injections by converting `<` `'` `>` `"` etc. into `&code;`


## Pagination

`'posts_per_page' => 9` or `query_posts('showposts=5');`



## If Array Key Exists

check for the presence of an array key, e.g. when validating a `select > option` value
```bash
if(!array_key_exists($key, $array));
```

## ElasticPress plugin

### Related Posts

```
ep_find_related(post_id, return_5);
```
