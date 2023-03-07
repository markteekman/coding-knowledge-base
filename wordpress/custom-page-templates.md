You can easily create a custom template page to have some fixed elements besides the CMS's content. Create a new file in the root of your theme folder and prefix that with `template-`, for example **template-our-story.php**. The first line in your template should contain the template name:

```php
<?php /* Template Name: Our Story */ ?>
```

To use the template, create a new page in your WordPress CMS and select your template under **Page > Summary > Template**. Use the following code as a base to get started:

```php
<?php /* Template Name: Our Story */ ?>  
  
<?php get_header() ?>  
  
<?php  
    if( have_posts() ) {  
        while( have_posts() ){  
            the_post();  
            the_content();  
        }  
    }  
?>  
  
<?php get_footer() ?>
```
