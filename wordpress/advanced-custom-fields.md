## Making a component
With ACF6 we can build our own custom 'blocks' which can be used in any WordPress page using the Gutenberg Editor. To create a new block from the theme folder go to `/blocks` and copy/past the **example** folder and rename it to your component, **counter** for example. The folder contains two files, `block.json` and `block.php`:

`block.json` is where you setup the global settings of your component, such as the `name`, `title` and `description`:

_blocks/counter/block.json_
```json
{  
    "name" : "acf/counter",  
    "title" : "Counter block",  
    "description" : "Counts from 0 to a given number.",  
    "style" : [  
        "file:./block.css"  
    ],  
    "category" : "formatting",  
    "icon" : "admin-comments",  
    "keywords" : [  
    ],  
    "supports" : {  
        "align" : false  
    },  
    "acf" : {  
        "mode" : "edit",  
        "renderTemplate" : "block.php"  
    }  
}
```

In `block.php` you build the actual component itself. Make sure you create a corresponding SCSS file in `src/scss/_counter.scss`:

_blocks/counter/block.php_
```php
<?php  
/**  
 * Counter Block Template. * * @param array  $block      The block settings and attributes.  
 * @param string $content    The block inner HTML (empty).  
 * @param bool   $is_preview True during backend preview render.  
 * @param int    $post_id    The post ID the block is rendering content against.  
 *                           This is either the post ID currently being displayed inside a query loop, *                           or the post ID of the post hosting this block. * @param array  $context    The context provided to the block by the post, or its parent block.  
 * * @package    Acato\Verstegen  
 * @subpackage Acato\Verstegen\Blocks  
 * @author     Mark Teekman <mark@acato.nl>, Marco de Rover <marco@acato.nl>, Joost Wiechers <joostwiechers@acato.nl>  
 */?>  
  
<div class="counters">  
   <div class="container">  
      <!-- content -->
   </div>  
</div
```

## Using a component
To see your component in action you have to create it within the WordPress admin. Follow these steps to see your component:

1. Go to **Custom Fields > Add new** and name your block, **Counter** in this example.
2. Go to **Settings** and set 'Show this field group if' equal to **Counter**
3. Now add your Block to a page and go to that page to view the Block
