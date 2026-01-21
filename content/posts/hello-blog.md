+++
date = '2026-01-21T09:34:02Z'
draft = false
title = 'Hello Blog'
+++

## A first blog post, while figuring things out

How does this display the text? I don't know... How do I deploy this blog? I don't know... How does Hugo work? I don't know...

But I want to figure it out and start this.

### Theme

```bash
echo "I hope it does format it well"
```

I'm going to try a few Hugo themes. I started with the paper theme, but I don't like thos colors and I think it was more then I wanted or needed.

The Console theme was kind of what I am looking for, but the code blocks didn't work as I expected.

After this I tried the Void theme but Hugo returned some compiling errors I didn't feel like troubleshooting...

As of now I am using the Archie theme.

```
this is A multiline code block

I would like to have it be colored black and be syntax highlighted

When no code language is specified it looks like it behaves normally
```

do `inline codeblocks` work as wel? They seem to work.

```powershell
# When there is a language specified it does some weird styling...
# I don't know why it does this

Write-Host "The syntax Highlighting seems to work"
Write-Host "But the styling is just weird"
```

---

I have used the above text as a way of validating the themes I tried. I think for now I will stick with Archie and try to customize it in the future.

Things I want to try to customize. But I'm not sure how flexible the themes are. I like the Archie theme a lot, but have some things I'd like to change.
In the future I'll try to figure out how I should go about changing the themes.

### A todo list before ending this post...

So my current to do's are:

- [ ] Figure out how to add pictures to a post
- [ ] Figuring out how to host the site after I build with Hugo
  - [ ] When figured out, making it an automated process after I write something, I only have to run one command or even none at all
- [ ] Git
  - [ ] Add this git repository to my github
  - [ ] Use git as intented and commit more changes.
- [ ] Customization
  - [ ] Footer Text
  - [ ] Theme colors
  - [ ] Possibly a dark mode?
  - [ ] circles at the bottom of the page don't have to be there in my opinion, but not sure if I'll be able to remove them 

---

### Git / Github

At the moment of writing this sentence this folder is initialized with git, but the repository has no remote origin. I want to upload this to my Github account.

To do this I created a Github repository named `blog.podepod.be`. With the commands below I added it as a remote origin and pushed the contents of the folder to Github.

```bash
git commit -m "init"
git branch -M main
git remote add origin https://github.com/Podepod/blog.podepod.be.git
```

When logging in to Github from the terminal I ran into an issue I always run into after not using Github for a while. Logging in with just a username and password does not work anymore. Which is a good thing security wise, but I always have to lookup how authenticating should be done... More of a me problem but still.

Figured it out again, and now I can commit and push without any problem.

### Hosting

As far as I can find, after you run the `hugo` command, the folder `./public` is generated. This is the full static site. This can be hosted a lot of ways, but the 2 main ones that stick out for me are Github Pages and Cloudflare Pages (under Build > Compute & AI > Workers & Pages)

I think I want to try and use one of those two options because the project should already be uploaded to GitHub and my DNS is already with Cloudflare.

#### Cloudflare Pages

I found documentation about Hugo in the cloudflare docs: [https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/) I also found some documentation in the cloudflare docs about adding a custom domain and disabling access to the default pages.dev domain: [https://developers.cloudflare.com/pages/configuration/custom-domains/](https://developers.cloudflare.com/pages/configuration/custom-domains/) The Cloudflare documentation looks very usefull and complete :) This should be very usefull when I eventually setup the Cloudflare pages project.
