### Consider the following scenario:

#### For all players in the NBA so far:

* A `player` custom post type exists with a meta field called `player_external_id`
  * Assume all players have a unique value in this field (different than the WordPress post ID)
  
#### For the upcoming season, all players will have a page on a 3rd party site with the following URL structure:

`http://www.nba-player-tv.com/channel/{player_external_id}`

* A new meta field `player_tv_url` was added to the `player` custom post
* All new players drafted for the upcoming season have the proper value set

#### Summary

| Type | Name |
| ---- | ---- |
| Custom Post Type | player |
| Custom Fields | player_external_id, player_tv_url |

### We need to update any missing `player_tv_url` post metadata

1. Write the code that would accomplish this.
1. How would you trigger the execution of this code?

**Answer 1:**
```php
<?php

$args = array(
    'post_type' => 'player',
    'meta_query' => array(
        array(
            'key'     => 'player_external_id',
            'value'   => ''
        )
    )
);
$query = new WP_Query( $args );

if ( $query->have_posts() )
{
    while ( $query->have_posts() )
    {
        $query->the_post();
        $post_id = get_the_ID();
        $player_tv_url = get_post_meta($post_id, 'player_tv_url')

        update_post_meta(
          $post_id, 
          'player_external_id', $player_tv_url 
        );
    }
}
```

**Answer 2:**
It would depend on who the end-user is. Some options include adding a custom UI button to trigger the function on a custom menu page (like in question 2), or a per post with post type "player" (like in question 2) or at {site_url}/wp-admin/edit.php?post_type=player index screen. It could also be done as one time chron job or via a separate app that uses the WordPress REST API.

