Breadcrumbs are generated using the Yoast SEO plugin. Enable the setting in **Yoast SEO > Settings > Advanced > Breadcrumbs > Enable breadcrumbs for your theme**. Then use this code block in your files:

```php
<?php  
    if ( function_exists( 'yoast_breadcrumb' ) ) {  
        yoast_breadcrumb( '[before_here]', '[after_here]' );  
    }  
?>
```

`[before_here]` and `[after_here]` are places to set HTML before and after the breadcrumbs. This can be used to define a wrapper which in turn can be used to style your breadcrumbs, for example a `<nav aria-label="Breadcrumbs navigation">`.
