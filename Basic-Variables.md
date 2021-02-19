## Basic Variables
  
  |Variable|Description|
  |---|---|
  |`{Title}`|The HTML-safe title of your blog.|
  |`{Description}`|The description of your blog. (may include HTML.)|
  |`{MetaDescription}`|The HTML-safe description of your blog.<br>e.g., `<meta name="description" content="{MetaDescription}"/>`|
  |`{BlogURL}`|Main URL of your blog.|
  |`{RSS}`|RSS feed URL for your blog.|
  |`{Favicon}`|Favicon URL for your blog.|
  |`{CustomCSS}`|Any custom CSS code added on your [Customize](https://www.tumblr.com/customize/) page.<br>This is added at the end of the CSS stylesheet.|
  |`{block:PermalinkPage}`<br>`{/block:PermalinkPage}`|Rendered on post permalink pages.<br>Usefull for embedding comment widgets.|
  |`{block:IndexPage}`<br>`{/block:IndexPage}`|Rendered on index (post) pages.|
  |`{block:HomePage}`<br>`{/block:HomePage}`|Rendered on the main post page.|
  |`{block:PostTitle}`<br>`{PostTitle}`<br>`{/block:PostTitle}`|Rendered on permalink pages. (Useful for displaying the current posts's title in the page title.)<br>Example: `<title>{Title} {block:PostTitle} - {PostTitle} {/block:PostTitle}</title>`|
  |`{block:PostSummary}`<br>`{PostSummary}`<br>`{/block:PostSummary}`|Identical to `{PostTitle}`, but will automatically generate a summary if a title doesn't exist.|
  |`{PortraitURL-16}`|Portrait photo URL for your blog. 16-pixels by 16-pixels.|
  |`{PortraitURL-24}`|Portrait photo URL for your blog. 24-pixels by 24-pixels.|
  |`{PortraitURL-30}`|Portrait photo URL for your blog. 30-pixels by 30-pixels.|
  |`{PortraitURL-40}`|Portrait photo URL for your blog. 40-pixels by 40-pixels.|
  |`{PortraitURL-48}`|Portrait photo URL for your blog. 48-pixels by 48-pixels.|
  |`{PortraitURL-64}`|Portrait photo URL for your blog. 64-pixels by 64-pixels.|
  |`{PortraitURL-96}`|Portrait photo URL for your blog. 96-pixels by 96-pixels.|
  |`{PortraitURL-128}`|Portrait photo URL for your blog. 128-pixels by 128-pixels.|
  |`{CopyrightYears}`|Displays the span of years your blog has existed.|
  
  ---
  
  ### Human explanation
  These variables are pretty universal in that they can be used for any theme and in HTML, CSS, and JavaScript code.
  
  `{Title}`:
  > The HTML-safe title of your blog.
  
  1. `{Title}` by itself is usually used in the `<title>` tag of the theme. If the current page is the blog's main page (Example: blog.tumblr.com), the title comes from the **Title** section of the Theme Editor page. Filling in that section then changes the browser('s tab) label to be what is entered in that section.
  	
		`{Title}` elsewhere is what is entered in the **Title** section to be displayed somewhere on the page in sight. For example, `<h1>{Title}</h1>` at the top of the page to title the blog's home page.
  	
  2. `{Title}` used in the Text and Chat post types will append the title of the blog's page *if* `{block:Title} {Title} {/block:Title}` exists for the post types.
  	
		Appending will occur if something like `<title>{Title} {block:PostTitle} - {PostTitle} {/block:PostTitle}</title>` exists. The resulting rendering, by that example, would be "Witty Blog Title - omg i cannot LITCHILLY believe it!!!".  
  	
		If `{block:PostTitle} - {PostTitle} {/block:PostTitle}` does not exist in the `<title>` tag, then only the title of the blog will be in the page's label, even if a Text or Chat post has been explicitly given a title during creation.
  	
		To have the Text and Chat post types' titles to be a part of the post page's title:
		
  		1. `{block:Title} {Title} {/block:Title}` must exist for the Text and Chat post types.
  		
			Example:
  		```
  		{block:Text}
  			{block:Title}
  				<span id="title">{Title}</span>
  			{/block:Title}
  			<span id="post-body">{Body}</span>
  		{/block:Text}
  		```
			
  		2. `{block:PostTitle} {PostTitle} {/block:PostTitle}` must exist in the `<title>` tag.
  
  ***HTML elements in the Title section will not be rendered, as given by "HTML-safe".***
  
  ---
  
  `{Description}`:
  > The description of your blog. (may include HTML.)
  
  The description comes from the **Description** section of the Theme Editor page. This is what one would enter as the blog's description.
  
  The "may include HTML" part means that HTML elements entered in the **Description** section will render. External links are such HTML elements that can be rendered.
  
  If `{Description}` is within `{block:ShowDescription} {/block:ShowDescription}` or `{block:HideDescription} {/block:HideDescription}`, then the appropriate setting in the Theme Editor page for displaying the Description will affect whether the Description in the **Description** section will display or will not display on the page.
  
  *`{Description}` is also used for the Link post types when it is enclosed in `{block:Description} {/block:Description}`. The name of the variable is somewhat misleading; the description of a Link post is simply what one would see as the *body* of the post.
  
  ---
  
  `[MetaDescription}`:
  > The HTML-safe description of your blog.
  
  Similar to `{Description}`, but does not render HTML elements.
  
  This can be used in the `<meta>` tag for a description that shows in the results page of a search engine. 
  Example: `<meta name="description" content="{MetaDescription}"/>`
  
  ---
  
  `{BlogURL}`:
  > Main URL for your blog.
  
  This renders the current URL that will be displayed in the address bar. This will also render the URL of the custom domain set on the blog, overriding the blog.tumblr.com URL convention.
  The rendered URL will include:
  * The forward slash (`/`) at the end of the URL
  * *http* or *https* at the beginning of the URL, dependent on the 'Always serve blog over SSL' setting.
  	* If the setting is set to 'off', the rendered URL will contain *http* in the URL. If the setting is set to 'on', the rendered URL will contain *https* in the URL.
  
  If a custom domain is set, the 'Always serve blog over SSL' setting will be unavailable. Serving the blog over SSL or another encrypted channel may then be dependent on whether the vendor of the custom domain offers encryption.
  <u>Author's Note: Someone should see if it is possible to obtain a custom domain that serves over an encrypted channel, and then see if `{BlogURL}` renders that custom domain with *https* in the URL.</u>
  
  `{BlogURL}` can be used in the `<a>` tag (For example, as `<a href="{BlogURL}ask">Ask</a>` (which would render as http[s]://blog.tumblr.com/ask)), but is (or can [CONSIDER LATER]) optional. Preceding the extra page with the forward slash (`/`) will do the same as if the extra page were preceded with `{BlogUrl}`. 
  
  | Input | Output URL |
  | --- | --- |
  | `<a href="{BlogURL}ask">Ask</a>` | <u>http[s]://blog.tumblr.com/</u>ask |
  | `<a href="/ask">Ask</a>` | <u>http[s]://blog.tumblr.com</u>/ask |
  
  The subtle difference between the two can be seen in the HTML editor. If `{BlogURL}` is used, the links in the Preview pane will include the target blog URL before *.tumblr.com*. If `/page` is used, then the links in the Preview pane will direct to http[s]://assets.txmblr.com. The former method will be openable links that open in a new tab. The latter method will be clickable links like the former, but do not open a page. 
  
  `{BlogURL}` is not strictly prohibited outside of the `<a>` tag. `{BlogURL}` could be used as a visible piece of text that has some purpose of being copy and pasted, while ensuring that what a user does with that visible piece of text is updated with a new URL or with a custom domain at the time of sight. It is not possible for `{BlogURL}` to change the pasted URL from elsewhere on the Internet to a newly-updated URL.
  
  ---
  
  `{RSS}`:
  > RSS feed URL for your blog.
  
  As what it says.
  This is implemented in the `<link/>` tag within the `<head>` tag as `<link rel="alternate" type="application/rss+xml" href="{RSS}"/>`.
  
  The RSS page is accessed through http[s]://[Blog URL]/rss link. Use an RSS reader to utilise the RSS feature.
  
  ---
  
  `{Favicon}`:
  > Favicon URL for your blog.
  
  As what it says.
  
  A favicon, short for "favorite icon", also known as 'shortcut icon', 'website icon', 'URL icon', or 'bookmark icon', is an icon that represents a website through a small icon next to the URL or tab of the website.
  The `{Favicon}` variable for a tumblr blog is dependent on the chosen avatar image from the *Edit appearance* function of the https://www.tumblr.com/settings/blog/[blog] page or the Avatar selector of the Theme Editor.
  The URL of the favicon is pseudo-randomly generated. Search for the URL of the favicon by using the Inspect Element feature of the web browser on a page of the blog, pressing Ctrl+F to begin searching the web document, and typing "shortcut icon". The line that is in the `<head>` tag contains the URL of the favicon. The dimensions of the favicon are expected to be 128 by 128.
  
  The `{Favicon}` variable is used in the `<link/>` tag within the `<head>` tag as `<link rel="shortcut icon" href="{Favicon}"/>`.
  
  ---
  
  `{CustomCSS}`:
  > Any custom CSS code added on your [Customize](https://www.tumblr.com/customize/) page.
  
  This is generally always added at the end of the CSS stylesheet. This can be used so users can change bits of a theme without altering the core code, which would risk the theme to become a "Custom theme" that will not receive any updates from the Theme Garden. Consider adding a comment at the near-top of the code that tells the user to use the `{CustomCSS}` function to change the look of the theme while providing some kind of documentation or method for anyone to look over to understand the code better.
  Custom CSS is added in the Advanced options page of the Theme Editor, and then under the "ADD CUSTOM CSS" section.
  
  One can choose to put `{CustomCSS}` in the middle of the style sheet to limit what users can change in the theme (assuming the core rules of the theme are situated below the `{CustomCSS}` variable, and the freely-editable rules are above the variable; this is to take advantage of the normal behaviour of CSS where rules at the bottom of the stylesheet "cascade" [CSS stands for 'Cascading Style Sheets'], or override, above rules with the same property, but may have a different value.).
  
  ---
  
  `{block:PermalinkPage} {/block:PermalinkPage}`:
  > Rendered on post permalink pages.
  > Useful for embedding comment widgets.
  
  This pair contains code that is shown in the permalink pages of posts. (https://blog.tumblr.com/post/...), but not elsewhere on the blog.
  
  The "Useful for embedding comment widgets" part means that the pair can be used for implementing Disqus and other similar widgets on the permalink pages of posts, especially if those widgets are meant to be only on permalink pages of posts. 

---

`{block:IndexPage} {/block:IndexPage}`:
> Description:
> *Rendered on index (post) pages.*

---

`{block:PostTitle} {PostTitle} {/block:PostTitle}`:
> Description:
> *Rendered on permalink pages. (Useful for displaying the current post's title in the page title)*

---

`{block:PostSummary} {PostSummary} {/block:PostSummary}`
> Description:
> *Identical to `{PostTitle]`, but will automatically generate a summary if a title doesn't exist.*

---

`{PortraitURL-[16, 24, 30, 40, 48, 64, 96, 128]}`:
> Description:
> *Portrait photo URL for your blog. [16, 24, 30, 40, 48, 64, 96, 128]-pixels by [16, 24, 30, 40, 48, 64, 96, 128]-pixels.*

---

`{CopyrightYears}`
> Description:
> *Displays the span of years your blog has existed.*

The years displayed span from the year the blog was created to the current year that the blog is being viewed.
