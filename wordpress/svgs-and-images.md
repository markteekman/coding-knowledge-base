## SVG

SVG's can be called using a Tool. Add this snippet at the top of the file you want to import an SVG:

```php
<?php
...
use Acato\ProjectName\Tools;
?>
```

To use this SVG in a template add the following code to call an SVG images from the `/svg` folder:

```php
<?php Tools::svg( 'svg-file-name' ); ?>
```

## Img

To use images from the `/src/images` (which are rendered to `/dist/images`) use the following `get_stylesheet_directory_uri()` WordPress function:

```php
<img src="<?php echo get_stylesheet_directory_uri(); ?>/dist/images/image.png" alt="" />
```

For a CSS background it's relative to the dist folder, so in most cases you'll use this path:

```scss
background-image: url("../images/image.png");
```
