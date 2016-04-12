# Connecting to netlify

## Step 1: Add Your New Site

![step 1 - add](https://cloud.githubusercontent.com/assets/6520639/9803638/717820a6-57d9-11e5-838f-d2a732eb0a41.png)

Creating a new site on netlify is simple. Once you’ve logged in, you'll be taken to https://app.netlify.com/sites. If you’re just starting out, there’s only one option.

## Step 2: Link to Your GitHub

Clicking “New Site” brings you to this screen:

![step 2 - link](https://cloud.githubusercontent.com/assets/6520639/9803637/7176ac8a-57d9-11e5-9b09-f43dc772a4f9.png)

When you push to GitHub, netlify does all the work. No more manual deploying of updates or changes!

Since your assets are hosted on GitHub, we’ll need to link netlify to GitHub. Click “Link to GitHub”.

## Step 3: Authorize netlify

![step 3 - authorize](https://cloud.githubusercontent.com/assets/6520639/9803635/71760370-57d9-11e5-8bdb-850aa176a22c.png)

It’s time to allow netlify and GitHub to talk to each other. Clicking the “Authorize Application” button will do just that. Like it says in the image below, netlify doesn’t store your GitHub access token on our servers. If you’d like to know more about the permissions netlify requests and why we need them, you can visit [https://docs.netlify.com/github-permissions/](https://docs.netlify.com/github-permissions/).

## Step 4: Choose Your Repo

![step 4 - repo](https://raw.githubusercontent.com/munkymack/netlify-assets/master/Step4Gatsby.png)

Now that you’ve connected netlify and GitHub, you can see a list of your Git repos. Select the repo that you'd like to connect to netlify.

## Step 5: Configure Your Settings

![step 5 - configure](images/Configuredeploy.png)

Here you can configure your options. Below are some examples of configuring your site for common build tools:

Build Tool | Directory | Command
-----------|-----------|--------------
Jekyll     | _site     | jekyll build
Grunt      | dist      | grunt build
Middleman  | build     | middleman build
Roots      | public    | roots compile
Hugo       | public    | hugo
Gatsby     | public    | gatsby build
Nanoc     | output      | nanoc
Punch       | output    | punch g
Assemble    | _gh_pages | grunt assemble
Gitbook     | _book/    | gitbook build
Docpad  | /out | docpad generate
Ember | /dist | ember build -e production
AngularJS | /dist| grunt build
Wintersmith | build/ | wintersmith build
Expose | images/_site | cd images && ../expose/expose.sh
Hexo | /public | hexo generate
Brunch | /public | brunch build
Pelican | /output | pelican content


For **Jekyll hosting**, make sure you have a Gemfile and a Gemfile.lock checked into your repository, specifying the Jekyll version you want to use.

For **Roots hosting**, make sure you add `roots` to your package.json.

For **Hugo hosting**, `hugo` will build and deploy with the latest version of `hugo`. You can specify a specific `hugo` release like this: `hugo_0.15`. Currently `0.13`, `0.14` and `0.15` are supported.

## Step 6: Build Your Site

![step 6 - build](https://cloud.githubusercontent.com/assets/6520639/9803640/717b9c40-57d9-11e5-9ca4-92f90f8ed005.png)

Now it’s time to sit back and relax. Go grab something cold to drink, scratch the dog behind the ears, or just get up and walk around (you’ve probably been in front of the computer for too long today, right?). Netlify will do the rest, and you can watch the progress.

## Step 7: Done

![step 7 - done](https://raw.githubusercontent.com/munkymack/netlify-assets/master/Step7Gatsby.png)
