---
title: Troubleshooting
---

This page lists some common issues that people often see and the corresponding solutions. If you find any bug not listed here, please [let us know](https://wpslimseo.com/contact/).

## Shortcodes not working

Sometimes, you have a shortcode in the post content or your page executes a special shortcode from a plugin like WooCommerce or EDD Invoices, and **you see a blank page** or **the shortcode doesn't work at all**.

The root cause might be that Slim SEO already parses the shortcodes when it tries to auto generate [meta description](/slim-seo/meta-description-tag/). If the shortcode has something related to session, custom logic, etc., then it might not work as expected.

To fix this problem, you can put the following snippet in your theme's `functions.php` file:

```php
add_filter( 'slim_seo_skipped_shortcodes', function( $shortcodes ) {
    $shortcodes[] = 'your_shortcode';
    return $shortcodes;
} );
```

## Blocks not working

Similar to shortcodes, some blocks might not working properly. To fix this problem, use the following snippet:

```php
add_filter( 'slim_seo_skipped_blocks', function( $blocks ) {
    $blocks[] = 'namespace/your-block-name';
    return $blocks;
} );
```
