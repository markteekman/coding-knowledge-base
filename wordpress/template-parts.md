## Building a template part
To make use of reusable components throughout templates (such as a different card types which are used in different locations) you can use partials. Partials are generally stored in the `/templates/parts/` folder. Partials always need a project prefix. It doesn't matter what it is as long as it's the same everywhere. In this example we use `$vrstgen_`. To create and use a basic `card.php` partial for example we can do the following:

_templates/parts/card.php_
```php
<?php
/**
 * @var array  $vrstgen_card           The card data.
 */
extract( $args, EXTR_SKIP );
?>

<a class="card--base card--product" href="<?php echo $vrstgn_card['url']; ?>">  
    <span class="card__image">  
        <?php echo wp_get_attachment_image( intval( $vrstgn_card['image'] ), 'rect-card', false, [ 'class' => 'card__image' ] ); ?>  
    </span>  
    <span class="card__content">  
        <?php if (isset($vrstgn_card ['h3']) && $vrstgn_card ['h3'] === true): ?>  
            <h3><?php echo wp_kses_post( $vrstgn_card['title'] ); ?></h3>  
            <?php else: ?>  
            <h2><?php echo wp_kses_post( $vrstgn_card['title'] ); ?></h2>  
        <?php endif ?>  
        <p><?php echo wp_kses_post( $vrstgn_card['excerpt'] ); ?></p>  
        <span class="btn btn--5">Go to product</span>  
    </span>  
</a>
```

> _**NOTE:**  `wp_kses_post` is used to sanitize the input._

> _**NOTE:**  You only have to have arguments if a partial is dynamic. If it's static you can just have the static data in the component itself._

## Using a template part
Now that you've created a partial you can use it in a template, either statically:

_archive-product.php_
```php
<div class="cards-container">
		<?php  
		$args = compact( 'vrstgn_card' );  
		get_template_part( 'templates/parts/card', 'image', $args );  
		?>  
		<?php  
		$args = compact( 'vrstgn_card' );  
		get_template_part( 'templates/parts/card', 'image', $args );  
		?>
</div>
```

Or dynamically in a loop:

```php
<?php  
if ( have_posts() ) {  
 while ( have_posts() ) {  
  the_post();  
  $vrstgn_card = [  
		'h3'       => true
   'url'       => get_the_permalink(),  
   'image'     => get_post_thumbnail_id(),  
   'title'     => get_the_title(),  
   'excerpt'   => get_the_excerpt()  
  ];  
  
  $args = compact( 'vrstgn_card' );  
  get_template_part( 'templates/parts/card', get_post_type(), $args );  
 }  
}  
?>
```

The `get_template_part()` function is key here as it is used to get partials path. It consists of two parameters, the first looks for `templates/parts/card` and the second parameter for the type, for example `card-product.php`. You can also be more verbose and just set `image` or `product` as the second parameter.
