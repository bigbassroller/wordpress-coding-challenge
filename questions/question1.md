### Given a file `wp-content/plugins/hello-world.php` with the following content:

```php
<?php

add_filter('the_content', 'hello_world');

function hello_world ( $content ){
  return "<h1>Hello World</h1>" . $content;
}
```

### Answer the following questions:

1. Why can't I see this plugin when viewing https://my-site.com/wp-admin/plugins.php?
1. If enabled, what would this plugin do?

**Answer 1:**
A requirement for all WordPress plugins is a valid plugin header. The plugin header must be defined as a PHP comment at the top of your main PHP file. It does not need to exist in every file for your plugin, only the main PHP file. The header tells WordPress that your PHP file is a legitimate WordPress plugin and should be processed as such.

- Taken from the book "Professional WordPress Design & Development"

**Answer 2:**
Adds the inspiring words "Hello World" to the beginning of all posts content fields. That includes all pages, posts, and media attachments!