---
title: "Converting to Static"
description: ""
date: "2019-12-16T14:37:02-06:00"
thumbnail: ""
categories:
  - "Blog"
---

As you can see from the last post, this blog hasn't been updated in a while. For all intents and purposes, it's a static site.
So why not take this opportunity to test out static site generators?

For this, I'm [Hugo](https://gohugo.io/). There's been a lot of stuff going around with these, but I haven't had a chance to test them out.
A _dead_ blog is a perfect place for this.

So here goes.

## Blog Changes
Before I got started I needed to prep my WordPress blog. I had to disable the [Jetpack](https://jetpack.com/) plugin I was using. This is because I was using the image optimization there. What this did was pull local content from Jetpack's CDN, which was a great feature for Wordpress. The problem is, when I did the WordPress export, it still had those URLs linked to Jetpack instead of locally.

As a general rule, it might be a good idea to disable any plugins that modify content:
- Caching
- Minification
- Related/Top Posts
- etc.

## Comments
[Disqus](https://disqus.com) seemed to be the obvious way to go here. Not sure why I hadn't done this before. Seems like offloading comments to a third party would be a no-brainer.

I did have some issues importing the comments from WordPress it Disqus. The automatic import claimed to work, but I couldn't see the comments. I also tried manually importing comments; again, I didn't see anything.

Buried deep in a _video_ on Disqus, they mentioned that imports might take up to 24 hours to complete. So I'll have to revisit this in a day or two.

## Domain Changes
This is somewhat unrelated, but I wanted to go ahead and get it done on WordPress before moving over to Hugo.

I wanted to add back the `www` to my domain name. I won't get into details here, but using the `www` subdomain for your site makes certain DNS level features easier to manage.
- [Cloudflare](https://www.cloudflare.com/) set up is easier at certain hosts.
- You can take advantage of [Azure Front Door](https://docs.microsoft.com/en-us/azure/frontdoor/front-door-overview)
- Netlify [Custom domains](https://docs.netlify.com/domains-https/custom-domains/) are easier to set up.

I changed this in the WordPress settings, did a database search and replace and also added Apache 301 Rewrite rules. If I cared enough about Google ranking, I would have waited a few weeks for all of my pages to get reindexed, but it wasn't that serious.

Again, this is less to do with Hugo and more to do with my preference, but it may be something you want to think about. Because once your site goes static, changing this is a little more difficult, depending on where you're hosted.

## Exporting to Hugo
You can check out the [Migrate To Hugo](https://gohugo.io/tools/migrations/#wordpress) page for details on exporting your WordPress settings, but I was successful in using [wordpress-to-hugo-exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter). I just uploaded and hit export and I was done.

## Hugo Install
I'm just going to skip you to the [official documentation](https://gohugo.io/getting-started/installing/) for this. I'd also recommend doing some basic Hugo tutorials. Maybe you'll save yourself some of the headaches that I had.

After I installed Hugo, I created a new site `hugo new site my-blog`. Then I added the [Mainroad theme](https://themes.gohugo.io/mainroad/) to the `themes` folder.

After that, I copied the content of the export to the `content` folder and that was _almost_ it. The blog started showing up, kinda.

## Hugo Tweaks
Now this is where I had to do some tweaks to get this just the way I wanted. I'm sure this was due to a combination of my lack of Hugo experience and/or the theme I selected. But here goes anyway.

For some reason, my content export included the following file: `content/index.md`. This file appeared to be a page that didn't get exported right. I renamed this and then posts started showing up on the home page as I expected.

My next issue was that my main menu was empty. I just looked up the documentation on my theme to figure out how to get some high-level pages to show up on my menu. That was easy enough.

I noticed that some images on my posts weren't displaying correctly. When I looked at the actual markdown file, the images were still in HTML. Hugo, by default, doesn't display HTML from markdown files. I had to add this configuration to my config.toml file:

```toml
[markup.goldmark.renderer]
  unsafe= true
```

Now I had a slight issue with my permalinks. After doing the export, the posts were exported with a hardcoded URL or `slug` in WordPress terms. All the existing pages rendered well. However, when I created a new post, the generated URL was `site.com/posts/[filename-of-post]` instead of `site.com\[title]`. I had to tweak my permalinks a little bit. Now this is where it gets a bit fishy, due to my skipping a lot of Hugo docs, but this is what I ended up doing. I had to move all my posts from the `posts` to `post` folder. Also, I had to configure permalinks in my config file:

```toml
[permalinks]
  post = "/:title/"
```

I'm sure someone can point me to what I did wrong, but that's what I ended up having to do.
