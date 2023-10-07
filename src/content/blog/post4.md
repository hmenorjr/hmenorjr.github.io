---
title: "Static Site Builds with Contentful and Github Actions"
description: "A step-by-step guide based on experience and other resources."
pubDate: "Dec 20, 2020"
heroImage: "/github_plus_contentful.webp"
---

## Stage Setting
Static contents are managed using Contentful and able to set up a webhook from Contentful against a repository in Github so that we can rebuild the site on changes in Contentful. I need to input the access token in plain text into Contentful as a secret to give it access to the repository

### How I did it?
Used the following reference to achieve the goal by using a personal access token: https://www.contentful.com/blog/2020/06/01/running-static-site-builds-with-github-actions-and-contentful/

We don't need to do all those, just a few steps for the "machine_user" or "Bot"

## The Challenge
The token would have access to **ALL** private repositories (inside the organization). I would like to restrict access to a specific repository. For example, https://github.com/the-org/contentful-repository.

## Solution
To achieve this, we need to do the following:

1. Create an email address for the bot. Since we need this for step
2. Register the newly created user in Github.
3. Add the "Machine User" or Bot to the organization and provide repository access to only one specific repository.
4. Generate a personal access token for the "machine_user" account.

## Add The Bot as Collaborator to the Organization
After step 1 and step 2, it's time to configure the bot. For this example we will use Contentful Bot. The picture is Gir from the animated TV series _[Invader Zim](https://en.wikipedia.org/wiki/Invader_Zim)_.

![github bot account image](/github_bot_account.webp "github bot account image")

![github bot account in dashboard](/github_bot_account_dash.webp "github bot account in dashboard")

Make sure your "bot" have only one access which is the private repository.

![image of the permission of bot](/github_bot_permission.webp "image of the permission of bot")

## Generate the Personal Token for the Bot
You can achieve this by logging in as the Bot and go straight to the profile settings.

### Developer Settings
![image of developer settings](/developer_settings.webp "image of developer settings")

### Personal access tokens
![image of personal access token config](/personal_access_tokens.webp "image of personal access token config")

### Click on `repo`
![image of developer settings repository](/developer_settings_repo.webp "image of developer settings repository")

After this step, it showed the token. Copied it and sent it to the ticket reporter. Reporter confirmed that the bot/_[machine_user](https://docs.github.com/en/free-pro-team@latest/developers/overview/managing-deploy-keys#machine-users)_ worked as expected.

## Get Involved
Not a fan of paywall, but would appreciate a donation for some coffee... Or pizza. https://ko-fi.com/hmenorjr