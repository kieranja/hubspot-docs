# Blog related posts
Adds a listing of blog posts based off of a set of parameters shared by posts across blogs. Posts are selected based off of their relevancy to the set parameters. For an example usage of the optional post\_formatter parameter, see [Creating a related blog post listing with the blog related posts HubL tag.](/tutorials/creating-a-related-post-listing)

Please note this tag does not generate a page/post level editable module, it is entirely configured with HubL.

#### Example
```jinja2
{% related_blog_posts %}
{% related_blog_posts limit=2, blog_ids="1,2", tags="Sales enablement,Marketing", blog_authors="John Smith,Frank Smith", path_prefixes="/business-blog", start_date="2018-04-10", end_date="2018-04-10", blog_post_override="2783035366" %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""><!--related-blog-entries--></span>
<div class="hs-related-blog-module feedreader_box">
  <span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""></span>
  <div class="hs-related-blog-item">
    <span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""></span>
    <div class="hs-related-blog-item-text">
      <span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""><a class="hs-related-blog-title" href="//www.underseaband.com/business-blog/marketing-is-fun"><span>Marketing is fun</span></a></span>
      <div class="hs-related-blog-byline">by <span class="hs-related-blog-author">John Smith</span> <span class="hs-related-blog-posted-at">posted on</span> <span class="hs-related-blog-date">June 3, 2018</span>
      </div>
      <div class="hs-related-blog-byline">
        <p class="hs-related-blog-description">Learn how to make marketing fun!<a href="//www.underseaband.com/business-blog/marketing-is-fun">Read more</a></p>
      </div>
      <div class="hs-related-blog-byline">
        <span class="hs-related-blog-tags">Tags: Marketing</span>
      </div>
    </div>
  </div>
  <div class="hs-related-blog-item hs-with-featured-image">
    <div class="hs-related-blog-item-text">
      <a class="hs-related-blog-title" href="//www.underseaband.com/business-blog/sales-is-fun"><span>Sales is fun</span></a>
      <div class="hs-related-blog-byline">by <span class="hs-related-blog-author">Frank Smith</span> <span class="hs-related-blog-posted-at">posted on</span> <span class="hs-related-blog-date">June 7, 2018</span>
      </div>
      <div class="hs-related-blog-byline">
        <p class="hs-related-blog-description">Learn how to make sales fun!<a href="//www.underseaband.com/business-blog/sales-is-fun">Read more</a></p>
      </div>
      <div class="hs-related-blog-byline">
        <span class="hs-related-blog-tags">Tags: Sales enablement</span>
      </div>
    </div>
    <div class="hs-related-blog-item-image-wrapper"><img alt="" class="hs-related-blog-featured-image" src="//www.underseaband.com/hubfs/business-blog/sales-is-fun.jpg"></div>
  </div>
</div>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| blog_ids | Integer | The ID(s) of blog(s) to include posts from. Omit this parameter to use the default blog. | 
           
           | 
| blog_post_ids | String | The ID(s) of a blog posts to use when finding relevant blog posts to list (comma separated). This parameter should only be used when the widget is appearing on pages, as on blog posts, it will default to the post the widget is appearing on. | 
           
           | 
| blog_post_override | String | The ID(s) of a blog posts which should always show up in the returned listing, despite all other parameter values and filters (comma separated). | 
           
           | 
| limit | Integer |  The max number of blog posts to list. | 3 | 
| tags | String | The tag(s) that should be used to determine if a post is relevant (comma separated). If a blog post has one of these tags or a similar tag, the post’s relevancy is increased, improving its ranking in the listing. | 
           
           | 
| start_date | datetime | Earliest published date. | 
           
           | 
| end_date | datetime | Latest published date. | 
           
           | 
| blog_authors | String |  The name(s) of authors to include posts from (comma separated). | 
           
           | 
| path_prefixes | String | URL paths or subdirectories to include posts from (comma separated). If a blog post has a similar prefix in its path, the post’s relevancy is increased, improving its ranking in the listing. | 
           
           | 
| post_formatter | String | The name of a custom macro to render returned blog posts. The macro is passed three parameters which are the blogs blog post object to format, the count in the iteration of blog posts, and the total count of blog posts in the results. If not specified or set to “default”, the built-in formatter will be used to format each post. | default | 

