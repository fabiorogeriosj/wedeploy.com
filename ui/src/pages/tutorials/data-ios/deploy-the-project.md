---
title: "Deploy the Project"
description: "In this section, you'll learn how to save and get data on iOS using the WeDeploy Swift API Client."
buttonTitle: "I deployed the project"
tutorialTitle: "Getting started with WeDeploy Data on iOS"
parentId: "data-ios"
layout: "tutorial"
time: 50
weight: 6
---

#### Deploy the Project

Now the moment you have been waiting for - deployment!

###### Add a Git remote

Open up your terminal and go to the `tutorial-data-ios` folder. Then, add a git remote by running:

```xml
git remote add wedeploy http://git.wedeploy.com/<your-project-id>.git
```

###### Push first commit

The remote is now set up and you are ready to make your first commit! 

1. `git add .`
2. `git commit -m "Awesome commit"`
3. `git push wedeploy master`

If it is your first time pushing to WeDeploy's git, you will need to enter the email and password for your WeDeploy account.

Once you have pushed, WeDeploy will immediately start deploying your project.

<aside>

###### <span class="icon-16-star"></span> Pro Tip

You can always check the status of your deployment by going to the _overview_ section of your project's <a href="http://dashboard.wedeploy.com" target="_blank">dashboard</a>.

</aside>
