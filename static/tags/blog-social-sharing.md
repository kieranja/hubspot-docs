# Blog social sharing
Blog social sharing renders share counters on your blog posts (if enabled in Content Settings).

#### Example
```jinja2
{% blog_social_sharing "blog_social_sharing" %}
{% blog_social_sharing "blog_social_sharing" select_blog='359485112' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_blog_social_sharing" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_blog_social_sharing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="blog_social_sharing">
     <div class="hs-blog-social-share">
          <ul class="hs-blog-social-share-list">
               <li class="hs-blog-social-share-item hs-blog-social-share-item-twitter">
                     <a href="https://twitter.com/share" class="twitter-share-button" data-lang="en" data-url="http://designers.hubspot.com/blog" data-size="medium" data-text="">Tweet</a>
               </li>
               <li class="hs-blog-social-share-item hs-blog-social-share-item-linkedin">
                    <script type="IN/Share" data-url="http://designers.hubspot.com/blog" data-showzero="true" data-counter="right"></script>
                </li>
                <li class="hs-blog-social-share-item hs-blog-social-share-item-facebook">
                     <div class="fb-like" data-href="http://designers.hubspot.com/blog" data-layout="button_count" data-action="like" data-show-faces="false" data-share="true" data-width="120"></div>
                </li>
                <li class="hs-blog-social-share-item hs-blog-social-share-item-google-plus">
                      <div class="g-plusone" data-size="medium" data-href="http://designers.hubspot.com/blog"></div>
                </li>
          </ul>
      </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID | Species which blog is connected to the share counters. This parameter accepts arguments of either 'default' or a blog ID (available in the URL of the Blog dashboard). If you want to use your default blog, this parameter is unnecessary. | default | 
| downgrade_shared_url | Boolean | Use HTTP in the url sent to the social media networks. Used to preserve counts when upgrading domains to HTTPS only. | false | 

