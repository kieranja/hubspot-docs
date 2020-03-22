# Blog comments
A blog comments module renders the comments embed code on a blog template. This Javascript embed code loads the comments form and comments, based upon your configuration in Content Settings.

#### Example
```jinja2
Blog Comment Form module:
{% blog_comments "blog_comments" overrideable=False, label='Blog Comments' %}

Blog Comment Count module:
{% blog_comments "blog_comments" %}

Blog Comment listing for specific blog:
{% blog_comments "default_blog_comments" select_blog='359485112' %}
```

#### Output
```jinja2
Blog Commment Form Output:
<span id="hs_cos_wrapper_blog_comments" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_blog_comments"
    style="" data-hs-cos-general-type="widget" data-hs-cos-type="blog_comments">
    <div class="section post-footer">
        <div id="comments-listing" class="new-comments no-comments"></div>
        <div id="hs-comment-embed" style="display:none;"></div>
        <div id="comment-form" class="new-comments">
            <form novalidate="" accept-charset="UTF-8"
                action="https://api.hubapi.com/comments/v3/comment?portalId=311600" enctype="multipart/form-data"
                id="hsForm_d30edada-82e4-4a69-aaf4-a9d0376f37e6" method="POST" class="hs-form stacked"
                data-form-id="d30edada-82e4-4a69-aaf4-a9d0376f37e6" data-portal-id="311600"
                data-reactid=".hbspt-forms-0">
                <div data-reactid=".hbspt-forms-0.0:$0">
                    <div class="hs_email field hs-form-field" data-reactid=".hbspt-forms-0.0:$0.$email">
                        <label class="" placeholder="Enter your Email" for="email-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$0.$email.0">
                            <span data-reactid=".hbspt-forms-0.0:$0.$email.0.0">Email</span><span
                                class="hs-form-required" data-reactid=".hbspt-forms-0.0:$0.$email.0.1">*</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;" data-reactid=".hbspt-forms-0.0:$0.$email.1">
                        </legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$0.$email.$email">
                            <input id="email-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input" type="email"
                                name="email" required="" placeholder="" value=""
                                data-reactid=".hbspt-forms-0.0:$0.$email.$email.0">
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$1">
                    <div class="hs_website field hs-form-field" data-reactid=".hbspt-forms-0.0:$1.$website">
                        <label class="" placeholder="Enter your Website"
                            for="website-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$1.$website.0">
                            <span data-reactid=".hbspt-forms-0.0:$1.$website.0.0">Website</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$1.$website.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$1.$website.$website">
                            <input id="website-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input" type="text"
                                name="website" value="" placeholder=""
                                data-reactid=".hbspt-forms-0.0:$1.$website.$website.0">
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$2">
                    <div class="hs_comment field hs-form-field" data-reactid=".hbspt-forms-0.0:$2.$comment">
                        <label class="" placeholder="Enter your Comment"
                            for="comment-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$2.$comment.0">
                            <span data-reactid=".hbspt-forms-0.0:$2.$comment.0.0">Comment</span>
                            <span class="hs-form-required" data-reactid=".hbspt-forms-0.0:$2.$comment.0.1">*</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$2.$comment.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$2.$comment.$comment">
                            <textarea id="comment-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input" name="comment"
                                required="" placeholder=""
                                data-reactid=".hbspt-forms-0.0:$2.$comment.$comment.0"></textarea>
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$3">
                    <div class="hs_subscribe field hs-form-field" data-reactid=".hbspt-forms-0.0:$3.$subscribe">
                        <label class="" placeholder="Enter your Subscribe to follow-up comments for this post"
                            for="subscribe-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$3.$subscribe.0">
                            <span data-reactid=".hbspt-forms-0.0:$3.$subscribe.0.0"></span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$3.$subscribe.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe">
                            <ul class="inputs-list" data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0">
                                <li class="hs-form-booleancheckbox"
                                    data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0">
                                    <label for="subscribe-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                                        class="hs-form-booleancheckbox-display"
                                        data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0.0">
                                        <input id="subscribe-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input"
                                            type="checkbox" name="subscribe" value="true"
                                            data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0.0.0">
                                        <span data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0.0.1">Subscribe
                                            to follow-up comments for this post</span>
                                    </label>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$4">
                    <div class="hs_lifecyclestage field hs-form-field" style="display:none;"
                        data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage">
                        <label class="" placeholder="Enter your Lifecycle Stage"
                            for="lifecyclestage-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.0">
                            <span data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.0.0">Lifecycle Stage</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.$lifecyclestage">
                            <input name="lifecyclestage" class="hs-input" type="hidden" value="subscriber"
                                data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.$lifecyclestage.0">
                        </div>
                    </div>
                </div>
                <div class="hs_submit" data-reactid=".hbspt-forms-0.2">
                    <div class="hs-field-desc" style="display:none;" data-reactid=".hbspt-forms-0.2.0"></div>
                    <div class="actions" data-reactid=".hbspt-forms-0.2.1">
                        <input type="submit" value="Submit Comment" class="hs-button primary"
                            data-reactid=".hbspt-forms-0.2.1.0">
                    </div>
                </div>
                <input name="hs_context" type="hidden"
                    value="{&quot;rumScriptExecuteTime&quot;:1396.815,&quot;rumServiceResponseTime&quot;:7737.500000000001,&quot;rumFormRenderTime&quot;:187.17999999999938,&quot;rumTotalRenderTime&quot;:7738.14,&quot;rumTotalRequestTime&quot;:183.2549999999992,&quot;pageUrl&quot;:&quot;http://311600.hs-sites.com/-temporary-slug-5eccb1d9-1f1b-4bbd-8e19-00e198331b15?hs_preview=ALicr-ma-4312320350&quot;,&quot;pageTitle&quot;:&quot;HubSpot Sales Professional User Guide: HubSpot Sales Professional Overview&quot;,&quot;source&quot;:&quot;FormsNext-static-1.390&quot;,&quot;isHostedOnHubspot&quot;:true,&quot;timestamp&quot;:1479135449193,&quot;userAgent&quot;:&quot;Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36&quot;,&quot;referrer&quot;:&quot;&quot;,&quot;hutk&quot;:&quot;a525e671c25f6b108d25e08c892e359e&quot;,&quot;originalEmbedContext&quot;:{&quot;portalId&quot;:&quot;311600&quot;,&quot;formId&quot;:&quot;d30edada-82e4-4a69-aaf4-a9d0376f37e6&quot;,&quot;target&quot;:&quot;#comment-form&quot;,&quot;redirectUrl&quot;:&quot;http://www.hubspot.com/contact-sales/thanks/&quot;,&quot;pageId&quot;:&quot;23423&quot;,&quot;pageName&quot;:&quot;My great landing page&quot;,&quot;css&quot;:&quot;.your-custom-css {background-color: #fe7722}&quot;,&quot;requiredCss&quot;:&quot;.my-custom-error-msgs {border-radius: 3px;}&quot;,&quot;submitButtonClass&quot;:&quot;hs-button primary&quot;},&quot;recentFieldsCookie&quot;:{},&quot;pageId&quot;:&quot;23423&quot;,&quot;pageName&quot;:&quot;My great landing page&quot;,&quot;boolCheckBoxFields&quot;:&quot;subscribe&quot;,&quot;dateFields&quot;:&quot;&quot;,&quot;redirectUrl&quot;:&quot;http://www.hubspot.com/contact-sales/thanks/&quot;,&quot;smartFields&quot;:{},&quot;urlParams&quot;:{&quot;hs_preview&quot;:&quot;ALicr-ma-4312320350&quot;},&quot;formValidity&quot;:{},&quot;correlationId&quot;:&quot;55d71532-ab6b-4415-98f5-f3a16d7741c9&quot;,&quot;disableCookieSubmission&quot;:false}"
                    data-reactid=".hbspt-forms-0.3">
                <input type="hidden" id="id_portalId" name="portalId" value="311600"><input type="hidden"
                    id="id_contentId" name="contentId" value="4312320350">
                <input type="hidden" id="id_collectionId" name="collectionId" value="2224463151">
                <input type="hidden" id="id_contentAuthorEmail" name="contentAuthorEmail"
                    value="cstone@hubspot.com"><input type="hidden" id="id_contentAuthorName" name="contentAuthorName"
                    value="Christopher Stone">
                <input type="hidden" id="id_comment_verification_text" name="comment_verification_text"
                    value="Your comment has been received.">
                <input type="hidden" id="id_contentTitle" name="contentTitle"
                    value="HubSpot Sales Professional User Guide: HubSpot Sales Professional Overview">
                <input type="hidden" id="id_contentPermalink" name="contentPermalink"
                    value="http://311600.hs-sites.com/-temporary-slug-5eccb1d9-1f1b-4bbd-8e19-00e198331b15">
                <input type="hidden" id="id_contentCreatedAt" name="contentCreatedAt" value="1479135208000">
                <input type="hidden" id="id_formGuid" name="formGuid" value="d30edada-82e4-4a69-aaf4-a9d0376f37e6">
            </form>
        </div>
    </div>
</span>

Blog Comment Listing Module Output:

(function ($) {
    var commentsEmbedContext = {
        portalId: 327485,
        collectionId: 359485112,
        contentId: 2684120609,
        target: '#comments-listing.new-comments',
        showComments: true,
        showForm: true,
        commentVerificationText: "Your comment has been received.",
        embedScriptEnv: "prod",
        apiEnv: "prod",
        contentTitle: "Post title",
        contentCreatedAt: "1427849160000",
        contentPermalink: "http:\/\/designers.hubspot.com\/blog\/post-name,
        contentAuthorEmail: "dhunt@hubspot.com",
        contentAuthorName: "David Hunt",
        captchaRequired: true,
        captchaKey: "6Lc3uMsSAAAAAMjk4NIvPQK9_-ZLk2wBokFCo5Qt",
        maxThreadDepth: 3,
        formId: "8d42bb92-241b-4894-b853-1d5f6553daa0"
    };

    function loadComments() {
        if (window.hubspot && typeof window.hubspot.loadCommentsEmbed === 'function') {
            hubspot.loadCommentsEmbed(commentsEmbedContext.embedScriptEnv, function () {
                if (typeof window.hsEmbedComments === 'function') {
                    window.hsEmbedComments(commentsEmbedContext);
                }
            });
        } else {
            setTimeout(loadComments, 50);
        }
    }
    loadComments();
})(window.hsjQuery || jQuery);
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| limit | Integer | Sets maximum number of comments. | 5000 | 
| select_blog | 'default' or blog ID | Specifies which blog is connected to the comments embed. This parameter accepts arguments of either 'default' or a blog ID (available in the URL of the Blog dashboard). If want to use your default blog, this parameter is unnecessary. | default | 
| skip_css | Boolean | Setting this option to True will stop the blog comments CSS from loading.  | false | 

