## Building a partial
To make use of reusable components throughout templates (such as a different card types which are used in different locations) you can use partials. Partials are generally stored in the `/views/partials/` folder. Partials always need a project prefix. It doesn't matter what it is as long as it's the same everywhere. In this example we use `$asc_`. To create and use a basic `card.php` partial for example we can do the following:

_views/partials/card.php_
```php
<?php
/**
 * @var array  $asc_card           The card data.
 */
extract( $args, EXTR_SKIP );

<a class="card" href="<?php echo $asc_card['url']; ?>">
		<?php echo wp_get_attachement_image( intval( $asc_card['image'] ), 'rect-card', false, [ 'class' => 'card__image' ] ); ?>
		<h3><?php echo wp_kses_post( $asc_card['title'] ); ?></h3>
		<p><?php echo wp_kses_post( $asc_card['excerpt'] ); ?></p>
</a>
```

> _**NOTE:**  `wp_kses_post` is used to sanitize the input._

> _**NOTE:**  You only have to have arguments if a partial is dynamic. If it's static you can just have the static data in the component itself._

## Using a partial
Now that you've created a partial you can use it in a template:

_archive-news.php_
```php
<div class="cards-container">
		<?php foreach ( $asc_featured_posts as $asc_features_post ) {
				$asc_card = [
				   'url'   => get_the_permalink( $asc_featured_post ),
				   'image'     => get_post_thumbnail_id( $asc_featured_post ),
				   'title'     => get_the_title( $asc_featured_post ),
				   'excerpt'   => get_the_excerpt( $asc_featured_post )
				];
				
				$args = compact( 'asc_card' );
				get_template_part( 'views/partial/card', get_post_type(), $args );
		}
</div>
```

The `get_template_part()` function is key here as it is used to get partials path. It consists of two parameters, the first looks for `views/partial/card` and the second parameter for the type, for example `card-product.php`.
