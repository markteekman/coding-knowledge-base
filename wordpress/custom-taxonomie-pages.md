Custom [post types](archive-and-single-pages) such as `News` and `Products` can have their own custom taxonomies (can also be seen as custom categories). These in turn can have their own 'archive' pages to display all posts of that taxonomie.

You can register a new taxonomie in **components/class-taxonomies.php** within the `Taxonomies` class. First register it in the static `init()` function:

_components/class-posttypes.php_
```php
public static function init() {  
		self::register_taxonomy_product_type();  
		// ...
}
```
Then setup the private static function with the same name in the same file. This is where you 'connect' the taxonomie to the post type with `register_taxonomy_for_object_type`:

_components/class-posttypes.php_
```php
public static function register_taxonomy_product_type() {  
		$labels = array(  
				'name'          => _x( 'Product types', 'Taxonomy General Name', 'verstegen' ),  
				'singular_name' => _x( 'Product type', 'Taxonomy Singular Name', 'verstegen' ),  
		);  
		$args   = [  
				'labels'            => $labels,  
				'hierarchical'      => true,  
				'public'            => true,  
				'show_ui'           => true,  
				'show_admin_column' => true,  
				'show_in_nav_menus' => false,  
				'show_tagcloud'     => true,  
				'show_in_rest'      => true,  
				'rewrite'           => [  
						'slug'         => _x( 'product-type', 'Taxonomy slug', 'verstegen' ),  
						'with_front'   => false,  
						'hierarchical' => true,  
				],
		];  
		register_taxonomy( 'product-type', array( 'example' ), $args );  
		register_taxonomy_for_object_type( 'product-type', 'product' );  
}
```

## Taxonomie archive page
To set up a new archive page for all the taxonomies of the post type you must create a file with the following format in the root of the theme folder: `taxonomy-product-type-shoes.php` for example.

> _**NOTE:** A taxonomy `Product type` wil now show up in the CMS under that post type. Make sure to create taxonomies with the same name as you used in your file, in this case 'Shoes'._
