---
layout: post
title:  "Publishing a Roku Channel: Part III - Publishing a Private Channel"
date:   2014-11-28 12:37:55
categories: developers
---

In a [previous tutorial](http://dev.zype.com/posts/2014/11/28/develop-roku-app-with-zype-sdk/),
we described how to develop a Roku app using the Zype SDK and testing it locally.
In this tutorial, we will walk through how to publish a Private Roku Channel that you can
share immediately. If you are interested in publishing a Public Roku Channel, the steps are very similar, just you have to wait for Roku to approve your channel before it can be accessed
in the Roku Channel Store. It is recommended that you first publish a private channel, test the
channel out to beta users, and then publish the channel publicly.

Before starting this tutorial, we will assume that you have already tested a Roku App
locally and are a registered Roku developer.

**Step 1**

Log into your Roku developer account and click Manage My Channels

![step 1](http://i.imgur.com/K66GKpz.png)

**Step 2**

Click add Private Channel.

![step 2](http://i.imgur.com/GeJiK58.png)

**Step 3**

Fill out Channel Store information for your channel.

![step 3](http://i.imgur.com/HJqtL2G.png)

**Step 4**

Fill our Channel Descriptions for your channel. You will need to have an HD Poster
that is a 290 x 218 JPEG file and an SD Poster that is a 214 x 144 JPEG file.

![step 4](http://i.imgur.com/pFA3aHQ.png)

**Step 5**

You can optionally upload screenshots of your Roku Channel. Read the [Roku documentation](http://sdkdocs.roku.com/display/sdkdoc/Channel+Packaging+And+Publishing#ChannelPackagingAndPublishing-38GeneratingScreenshotsSincev31onRoku1andv43onRoku2) on how to generate a screenshot.

![step 5](http://i.imgur.com/lMtmsak.png)

**Step 6**

Last, you will need to upload your application package.

![step 6](http://i.imgur.com/xufsqQC.png)

Follow the instructions from the [Roku documentation](http://sdkdocs.roku.com/display/sdkdoc/Channel+Packaging+And+Publishing#ChannelPackagingAndPublishing-30PackagingYourApplication) on how to generate a key and then package your channel.

Once you have downloaded your Roku Channel package, upload the application package and click the "Publish" arrow. You will get an access code url that can be used to download the private
Roku channel on your individual Roku account.

**More tutorials in this series:**

Part I: [Creating a Roku Channel using the Zype Platform](http://dev.zype.com/posts/2014/11/25/create-roku-app-on-zype/)

Part II: [Developing the Roku Channel using the Zype SDK](http://dev.zype.com/posts/2014/11/28/develop-roku-app-with-zype-sdk/)
