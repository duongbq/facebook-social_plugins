# Facebook Social plugins

The Facebook Social plugins for Rails 3 consist of:

* Helper::View
* Helper::Script
* Helper::OpenGraph # see https://developers.facebook.com/docs/opengraph/

The `Helper::View` contains methods for inserting the HTML5 <div> elements for Facebook social plugins

The `Helper::Script` contains methods for inserting <script> snippets for Facebook integration, such as displaying the Social plugins with the Facebook layout/styling applied etc.

## Social plugins

Currently the following Social plugins are included in this gem

* Root
* Activity Feed
* Comments
* Facepile
* Like Box
* Like Button
* Live Stream
* Login Button
* Recommendations Box
* Registration
* Send Button
* Subscribe Button

(see more info below)

## Script Helpers

* async_init_script(app_id, domain, options = {})
* facebook_script(locale = :en)

The async_init_script requires the Facebook app_id, fx '753632322' and the domain name of the app, fx 'www.example.com'. You can also specify the channel file (will default to channel file in vendor/assets of this gem)

### Configuration scripts

* fb_async_init_script(app_id, domain)
* fb_channel_script(locale = :en_US)

### Login

* fb_login_click_react(options, &block)
* fb_login_react(options, &block)
* fb_onlogin_react(options, &block)
* fb_onlogin_redirect_to(path, options)

### Logout

* fb_logout_click_react(options, &block)
* fb_logout_react(options, &block)
* fb_onlogout_react(options, &block)
* fb_onlogout_redirect_to(path, options)

* fb_login_and_react(options = {:selector => '#fb_login_and_reload'})
* fb_logout_and_redirect_to(path, options = {:ready => false})

## Open Graph Helper

Convenience method to generate all header/meta tags for Facebook Open Graph

* open_graph_meta(name, namespace, app_id, object_type, options = {})

* `<head>` tag helper*

* og_header(name, namespace)

* `<meta>` tag helpers*

* og_type(app_id, object_type)
* og_title(title)
* og_image(image_url)
* og_url(href)
* og_desc(desc)
* fb_app_id(app_id)

## Extra View helpers

* fb_analytics(app_id) # Facebook analytics meta tag
* fb_activity(namespace, action) # Open Graph action to perform

* fb_onlogout(script) # setup FB event handler to trigger on FB logout
* fb_onlogout_redirect_to(path) # setup FB event handler to trigger on FB logout and redirect

## Social plugins

Currently the following Social plugins are included in this gem

* Root
* Activity Feed
* Comments
* Facepile
* Like Box
* Like Button
* Live Stream
* Login Button
* Recommendations Box
* Registration
* Send Button
* Subscribe Button

View methods exposed:

* fb_root
* fb_activity options = {}
* fb_add_to_timeline options = {}
* fb_comments options = {}
* fb_facepile options = {}
* fb_like_box (options= {}
* fb_like_button options = {}
* fb_live_stream options = {}
* fb_login_button options = {}
* fb_recommendations_box options = {}
* fb_registration options = {}
* fb_send_button options = {}
* fb_subscribe_button options = {}

Note: You don't have to worry about dashed or underscored properties. Conversions will be handled automatically. The Facebook Social plugins API is (sadly) not very consistent when it comes to attribute names.

Extras:

* fb_logout_button(options = {}) # renders logout button (english only)

Logout button options: 
html: (html options for anchor tag)
size: 'small' or 'large' (size of logout button img)

### Facebook root

```html
<div id="fb-root"></div>
```

A Facebook placeholder div

### Activity feed

```html
<div class="fb-activity" data-width="300" data-height="300" data-header="true" data-recommendations="false"></div>
```

* site - the domain for which to show activity; include just the full domain name, without http:// or a path. The XFBML version defaults to the current domain.
* action - a comma separated list of actions to show activities for.
* app_id - will display all actions, custom and global, associated with this app_id.
* width - the width of the plugin in pixels. Default width: 300px.
* height - the height of the plugin in pixels. Default height: 300px.
* header - specifies whether to show the Facebook header.
* colorscheme - the color scheme for the plugin. Options: 'light', 'dark'
* font - the font to display in the plugin. Options: 'arial', 'lucida grande', 'segoe ui', 'tahoma', 'trebuchet ms', 'verdana'
* border_color - the border color of the plugin.
* recommendations - specifies whether to always show recommendations in the plugin. 
* linktarget - This specifies the context in which content links are opened. 
* ref - a label for tracking referrals; must be less than 50 characters 
* max_age - a limit on recommendation and creation time of articles that are surfaced in the plugins, the default is 0 (days)

### Comments

```html
<div class="fb-comments" data-href="http://example.com" data-num-posts="2" data-width="470"></div>
```

href - the URL for this Comments plugin. News feed stories on Facebook will link to this URL.
width - the width of the plugin in pixels. Minimum recommended width: 400px.
colorscheme - the color scheme for the plugin. Options: 'light', 'dark'
num_posts - the number of comments to show by default. Default: 10. Minimum: 1
mobile - whether to show the mobile-optimized version. Default: auto-detect.

### Like box

```html
<div class="fb-like" data-send="true" data-width="450" data-show-faces="true"></div>
```

* href - the URL to like. The XFBML version defaults to the current page.
* send - specifies whether to include a Send button with the Like button. 
* layout - there are three options (standard, button_count, box_count)
* show_faces - specifies whether to display profile photos below the button (standard layout only)
* width - the width of the Like button.
* action - the verb to display on the button. Options: 'like', 'recommend'
* font - the font to display in the button. Options: 'arial', 'lucida grande', 'segoe ui', 'tahoma', 'trebuchet ms', 'verdana'
* colorscheme - the color scheme for the like button. Options: 'light', 'dark'
* ref - a label for tracking referrals; must be less than 50 characters and can contain alphanumeric characters
fb_ref - the ref parameter
fb_source - the stream type ('home', 'profile', 'search', 'ticker', 'tickerdialog' or 'other') in which the click occurred and the story type ('oneline' or 'multiline'), concatenated with an underscore.

### Live stream

```html
<div class="fb-live-stream" data-event-app-id="285193711555371" data-width="400" data-height="500" data-always-post-to-friends="true"></div>
```

### Login

```html
<div class="fb-login-button" data-show-faces="true" data-width="200" data-max-rows="1"></div>
```

* show-faces - specifies whether to show faces underneath the Login button.
* width - the width of the plugin in pixels. Default width: 200px.
* max-rows - the maximum number of rows of profile pictures to display. Default value: 1.
* scope - a comma separated list of extended permissions. 

### Registration

*Async Validation*

If you have to check something on your server (e.g. if a username is taken) then you don't have to reply from the validation function right away. You can return null (which is the default return in javascript) and then use the second parameter to reply with any errors. You have 20 seconds before the form submits anyways.

```html
<fb:registration redirect-uri="https://developers.facebook.com/tools/echo" 
  fields='[{"name":"name"},
           {"name":"username","description":"Username","type":"text"}]' 
  onvalidate="validate_async"></fb:registration> 

<script src="http://code.jquery.com/jquery-1.7.1.min.js"></script>
<script> 
function validate_async(form, cb) {
  $.getJSON('https://graph.facebook.com/' + form.username + '?callback=?', 
    function(response) {
      if (response.error) {
        // Username isn't taken, let the form submit
        cb();
      }
      cb({username: 'That username is taken'});
  });
}
</script> 
```

### Add to Timeline

```html
<div class="fb-add-to-timeline"></div>
```

Add to Timeline lets users create a lasting connection between your app and their Timeline on Facebook. When a user clicks Add to Timeline, your app can publish app specific actions to the user's Timeline. As users engage with your app over time, their actions become more prominently displayed on their Timeline. This can become an important part of how people express themselves on Facebook. The experience for users is seamless and fun and requires little effort for them to personalize their identity.

Add to Timeline plugin is available through the Javascript SDK via the <fb:add-to-timeline> XFBML tag.

There are two different display modes for the Add to Timeline: box (default) and button. You can also configure additional extended permissions for the plugin by adding the perms parameter.

* mode - the display mode - box (default) and button
* show_faces - whether to show faces


### Facepile

```html
<div class="fb-facepile" data-href="http://developers.facebook.com" 
  data-action="join" data-size="large" data-max-rows="1" data-width="300" 
  data-colorscheme="dark">
</div>  
```

The Facepile plugin displays the Facebook profile pictures of users who have connected with your page via a global or custom action, or can also be configured to display users that have signed up for your site.

If you want to display users who have connected to your page via an action, specify with the action parameter

To display users who have liked your page, specify the URL of your page as the href parameter. To display users who have signed up for your site, specify your application id as the app_id parameter.

* event-app-id - the app id for the event
* action - the action to perform, fx 'og_recipebox:planning_to_make'
* width - the width of the plugin in pixels. Minimum recommended width: 400px.
* href - the referenced page
* max_rows - max rows to display, 1-10 normally

### Recommendations

```html
<div class="fb-recommendations" data-width="300" data-height="300" data-header="true"></div>
```

* site - the domain to show recommendations for. The XFBML version defaults to the current domain.
* action - a comma separated list of actions to show recommendations for.
* app_id - will display recommendations for all types of actions, custom and global, associated with this app_id.
* width - the width of the plugin in pixels. Default width: 300px.
* height - the height of the plugin in pixels. Default height: 300px.
* header - specifies whether to show the Facebook header.
* colorscheme - the color scheme for the plugin. Options: 'light', 'dark'
* font - the font to display in the plugin. Options: 'arial', 'lucida grande', 'segoe ui', 'tahoma', 'trebuchet ms', 'verdana'
* border_color - the border color of the plugin.
* linktarget - This specifies the context in which content links are opened. By default all links within the plugin will open a new window. se to _top or _parent. 
* ref - a label for tracking referrals; must be less than 50 characters and can contain alphanumeric characters 
* max_age - a limit on recommendation and creation time of articles that are surfaced in the plugins, the default is 0 (days)

### Send button

```html
<div class="fb-send" data-href="http://example.com"></div>
```

* href - the URL to send.
* font - the font to display in the button. Options: 'arial', 'lucida grande', 'segoe ui', 'tahoma', 'trebuchet ms', 'verdana'
* colorscheme - the color scheme for the button. Options: 'light', 'dark'
* ref - a label for tracking referrals; must be less than 50 characters and can contain alphanumeric characters
* fb_ref - the ref parameter
* fb_source - the story type ('message', 'group', 'email') in which the click occurred.

### Subscribe button

```html
<div class="fb-subscribe" data-href="https://www.facebook.com/zuck" data-show-faces="true" data-width="450"></div>
```

* href - profile URL of the user to subscribe to. This must be a facebook.com profile URL.
* layout - there are three options (standard, button_count, box_count).
* show_faces - specifies whether to display profile photos below the button (standard layout only)
* colorscheme - the color scheme for the plugin. Options: 'light' (default) and 'dark'
* font - the font to display in the plugin. Options: 'arial', 'lucida grande', 'segoe ui', 'tahoma', 'trebuchet ms', 'verdana'
* width - the width of the plugin.

## Contributing to facebook-social_plugins
 
* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet.
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it.
* Fork the project.
* Start a feature/bugfix branch.
* Commit and push until you are happy with your contribution.
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

## Copyright

Copyright (c) 2012 Kristian Mandrup. See LICENSE.txt for
further details.
