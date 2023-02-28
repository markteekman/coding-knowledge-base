## Setting up an archive
To set up and archive page your first have to create one by making a new file in the themes root folder, for example **archive-news.php**. You then have to register this new archive page in **components/class-posttypes.php** within the `PostTypes` class. First register it in the static `init()` function:

_components/class-posttypes.php_
```php
public static function init() {  
	self::register_posttype_news();  

	// ...
}
```

Then setup the private static function with the same name:

_components/class-posttypes.php_
```php
/**  
 * Register Custom Post Type "news". * * @return void  
 */private static function register_posttype_news() {  
   $labels = self::expand_labels(  
      [  
         'name'          => _x( 'news', 'Post Type General Name', 'verstegen' ),  
         'singular_name' => _x( 'news', 'Post Type Singular Name', 'verstegen' ),  
      ]  
   );  
   $args   = [  
      'label'               => $labels['name'],  
      'description'         => __( 'For adding testimonials', 'verstegen' ),  
      'labels'              => $labels,  
      'supports'            => [ 'title', 'excerpt', 'editor', 'thumbnail' ],  
      'taxonomies'          => [ 'post_tag' ],  
      'hierarchical'        => false,  
      'public'              => true,  
      'show_ui'             => true,  
      'show_in_menu'        => true,  
      'menu_position'       => 5,  
      'menu_icon'           => 'dashicons-testimonial',  
      'show_in_admin_bar'   => true,  
      'show_in_nav_menus'   => true,  
      'can_export'          => true,  
      'has_archive'         => true,  
      'exclude_from_search' => false,  
      'publicly_queryable'  => true,  
      'capability_type'     => 'post',  
      'show_in_rest'        => true,  
      'rewrite'             => [  
         'slug'       => _x( 'news', 'Post-Type Slug', 'verstegen' ),  
         'with-front' => false,  
      ],  
   ];  
   register_post_type( 'news', $args );  
}
```

## Using the WordPress loop
Archive pages in WordPress are generally build up by using the default WordPress loop:

_archive-news.php_
```php
<?php
if (have_posts()) {
  while(have_posts()) {
    the_post();
  }
}
?>
```

You can set different functions and HTML after the `the_post()` function. To display all titles for example you can do the following:

_archive-news.php_
```php
<?php
if (have_posts()) {
  while(have_posts()) {
    the_post();
    the_title();
  }
}
?>
```

A kind of 'starter' loop could be defined using the following functions such as `the_permalink()`, `the_post_thumbnail`, `the_title()` and `the_excerpt()`:

_archive-news.php_
```php
<?php
if ( have_posts() ) {
   while ( have_posts() ) {
      the_post();
      ?>
      <a href="<?php the_permalink(); ?>">
         <?php the_post_thumbnail( 'thumbnail_size', [
            'class' => 'image__class--something'
         ] ); ?>

         <h2>
            <?php the_title(); ?>
         </h2>

         <p class="excerpt">
            <?php the_excerpt(); ?>
         </p>
      </a>
      <?php
   }
}
?>
```
