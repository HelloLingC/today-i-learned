---
title: 'Hugo Deploy Shell'
date: 2024-08-10T16:01:59+08:00
draft: false
categories:
tags: [hugo]
---

For a long time, I always used Hexo as my blogging generator. But when i switched to Hugo, the things're completely different. The deployment methods changed .

For now, if i wanna host my stuff on somethng like Github Pages, i should utillize so called "continuous deployment" which leverages on Github Action. I'm required to push my primitive content into remote repository, and let the remote finish the building process.

And the command `hugo deploy` unlike Hexo is only for deployment for Cloud storage like GCS, Azure Storage, etc...... I personally dislike this way. So this is why i wrote a shell script helping me deploy in the "legacy" way.

```
hugo --minify --gc
find ./deploy_git -mindepth 1 ! -path './deploy_git/.git*' -exec rm -r {} +
cp -r ./public/* ./deploy_git
cd deploy_git
git add .
git commit -m "OwO $(date "+%Y-%m-%d %H:%M:%S")"
git push origin master
```

I use `find` command with `mindepth 1` flag which means "Do not apply any tests or actions at levels less than levels". So the  `rm` action won't affect , in this case, the `./deploy_git` folder. `! -path` to exclude `.git` folder, `{}` is a placeholder which represents the files and directories that are found. `+` make the `rm` command being executed with as many arguments as possible at once, rather than executing the command separately for each found item.

This script'll recursively delete files inside `./deploy_git` which's a bit low-efficieny. But currently i have no idea how to add a file comparision system. I can predict its a time-consuming task, and really making a mountain out of a molehill.

# Tbh...

Using the recommended deploy method in the docs is pretty good, since your blog source will be backed up within the repo.

But...What if i have periodical backup in the local.

