### Consider the following code snippet

```php
<?php

add_action('admin_menu', 'custom_menu');

$custom_menu_string = __( 'Custom Menu' , 'nba');

function custom_menu(){
  add_menu_page($custom_menu_string, $custom_menu_string, 'manage_options', 'custom-menu', 'custom_menu_page_display');
}

function custom_menu_page_display(){
  ?>
    <h1>Hello World</h1>
    <p>This is a custom page</p>
  <?php
}
```

### Briefly explain

1. What does this code do?
1. Who can/cannot view its effects?
1. What URL exposes the new functionality?

**Answer 1:**
Adds a custom menu page to the wp-admin section.

**Answer 2:**
A user, typically an Administrator with the capability to "manage_options".

**Answer 3:**
{site_url}/wp-admin/admin.php?page=custom-menu
