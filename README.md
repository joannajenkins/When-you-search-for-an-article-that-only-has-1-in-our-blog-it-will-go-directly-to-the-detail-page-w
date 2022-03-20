# When-you-search-for-an-article-that-only-has-1-in-our-blog-it-will-go-directly-to-the-detail-page-w
When you search for an article that only has 1 in our blog, it will go directly to the detail page without going through the search results page.
// Redirect to post if there is only one search result
add_action('template_redirect', 'single_search_redirect');
function single_search_redirect()
{
    if (is_search()) {
        global $wp_query;
        if ($wp_query->post_count == 1) {
            wp_redirect(get_permalink($wp_query->posts['0']->ID));
        }
    }
}
