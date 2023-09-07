# post_read_time
How to count post_read_time in WordPress without using plugins

# 1. Functions.php file.
<p>// Function to calculate post read time<br />function calculate_post_read_time() {<br />$content = get_post_field('post_content', get_the_ID());<br />$word_count = str_word_count(strip_tags($content));<br />$reading_time = ceil($word_count / 100); // Assuming an average reading speed of 200 words per minute<br />return $reading_time;<br />}</p>
<p>// Function to display post read time<br />function display_post_read_time() {<br />$read_time = calculate_post_read_time();<br />echo 'Estimated reading time: ' . $read_time . ' minutes';<br />}</p>
<p>// Add a shortcode to display read time in posts or pages<br />add_shortcode('post_read_time', 'display_post_read_time');</p>

# 2. Then, copy the code below and paste it into single.php file in the while loop.
<p>&lt;?php echo do_shortcode('[post_read_time]'); ?&gt;</p>
