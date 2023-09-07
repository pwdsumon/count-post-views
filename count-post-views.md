# count-post-views
How to count post views in WordPress without using plugins

# 1. Functions.php file.

<p>function gt_get_post_view() {<br />$count = get_post_meta( get_the_ID(), 'post_views_count', true );<br />return "$count views";<br />}<br />function gt_set_post_view() {<br />$key = 'post_views_count';<br />$post_id = get_the_ID();<br />$count = (int) get_post_meta( $post_id, $key, true );<br />$count++;<br />update_post_meta( $post_id, $key, $count );<br />}<br />function gt_posts_column_views( $columns ) {<br />$columns['post_views'] = 'Views';<br />return $columns;<br />}<br />function gt_posts_custom_column_views( $column ) {<br />if ( $column === 'post_views') {<br />echo gt_get_post_view();<br />}<br />}<br />add_filter( 'manage_posts_columns', 'gt_posts_column_views' );<br />add_action( 'manage_posts_custom_column', 'gt_posts_custom_column_views' );</p>

# 2. Then, copy the code below and paste it into single.php file in the while loop.
<p>&lt;?php gt_set_post_view(); ?&gt;</p>

# 3. Next, copy the following code and paste it where you want to show the number of views
<p>&lt;?= gt_get_post_view(); ?&gt;</p>
