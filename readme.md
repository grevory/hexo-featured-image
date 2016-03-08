title: Featured Image
tags:
---

# Hexo Featured Image

A Hexo plugin to allow adding featured images with `featured_image` in front-matter and using it in post or have it output in the content.json if used together with [hexo-generator-json-content](https://github.com/alexbruno/hexo-generator-json-content).

For example:

`CoolPost.md`

	---
	title: Cool post
	featured_image: my_img.png
	---
	What a cool blog I have!

By using the Hexo Front Featured Image plugin, you can specify a post's featured image in its front matter.


The absolute path to `my_img.png` will be available through `post.featured_image` in your templates.

For example:

`article.ejs`
```
	...
	<% if (post.featured_image){ %>
        <img src="<%- post.featured_image %>">
    <% } %>
    ...
```

## Configuration
### URL
For this plugin to work correctly, you must set `url` to your URL in `_config.yml`. For example, if you are working locally using the default url (http://0.0.0.0:4000/), set it like this:

`_config.yml`
```
	...
	# URL
    url: http://0.0.0.0:4000/
    ...
```
### post_asset_folder
This plugin works without configuration if you are using [post asset folders](https://hexo.io/docs/asset-folders.html), or you are storing your images in `source/images`.

If you are not using post asset folders, and you prefer to store your images somewhere else than in `source/images`, you must specify `image_dir` in `_config.yml` to wherever you store your images. To set your image directory to `source/assets`, you would set `image_dir: assets` in `_config.yml`. Example:

`_config.yml`
```
	...
	# Directory
    source_dir: source
	public_dir: public
    ...
    image_dir: assets
    ...
```

### [hexo-generator-json-content](https://github.com/alexbruno/hexo-generator-json-content)
This plugin plays nicely with [hexo-generator-json-content](https://github.com/alexbruno/hexo-generator-json-content), and will output the absolute path of `featured_image` to `content.json` if `featured_image` has been set to `true` in the `jsonContent` configuration part of `_config.yml` like so:
```
	...
    jsonContent: {
    	...
        posts: {
        	...
            featured_image: true
        }
    }
```