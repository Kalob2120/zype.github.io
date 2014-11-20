---
layout: post
title:  "Uploading Videos With the Zype Command Line Interface"
date:   2014-11-20 10:37:55
categories: developers
---

We're rolling out a bunch of new ways to add video content to the Zype Platform, like [Youtube Channel Import](http://dev.zype.com/posts/2014/11/18/search-youtube-in-zype/) and [Crunchyroll Video Import](http://dev.zype.com/posts/2014/11/19/adding-crunchyroll-as-a-video-source/). In this post we'll show you how to use the Zype Command Line Interface (or CLI) to upload videos that you have stored on a harddrive.

### Downloading and Installing the Zype CLI

First, you'll need to download and set up the Zype CLI. You can find the tool on [gitHub](https://github.com/edla/zype-cli).

![gitHub](http://i.imgur.com/ZC3mLEs.png)

You'll need to clone down the repo, then run the following commands:

<pre><code>$ gem build zype.gemspec
</code></pre>

<pre><code>$ gem install ./zype-1.0.0.gem
</code></pre>

You can confirm that your installation succeeded by entering

<pre><code>$ zype
</code></pre>

which will display a list of available commands for the Zype CLI. Remember this command in case you have questions about what the Zype CLI can do!

![CLI Interface](http://i.imgur.com/YZ8gcJl.png)


### Logging in through the Zype CLI

Let's make sure that you can login and that your Zype CLI is linked to your instance of the Zype Platform.

Enter the command below:

<pre><code>$ zype account:login
</code></pre>

You'll be prompted to enter your Zype API Key. You can find this by logging in to the [Zype Platform](https://admin.zype.com) and clicking on API within the settings menu at the top of the screen. Grab your API key and enter it into the terminal to continue.

### Uploading your videos

You'll need to know which directory contains the videos you want to upload. Once you know where they live, you can run the upload command.

If all of the files live in a single directory, run the following command, replacing the example directory ("/myDir/videos") with your own.

<pre><code>$ zype video:upload --directory="/myDir/videos"
</code></pre>

If you have multiple subdirectories that contain videos, you can pass in a wildcard character (*) at the end of the parent directory to grab all of the videos within each subdirectory. Like this:

<pre><code>$ zype video:upload --directory="/myDir/videos/*"
</code></pre>

Now sit back while we upload all of your videos and add them to the Zype Platform as video imports. Once we've imported all of your videos you will find them under the [Video Imports](https://admin.zype.com/video_imports) tab. The last step is to create new videos from the imports or add the video imports to videos you already have on the Zype Platform.

![video imports](http://i.imgur.com/SrnGXnw.png)

### Confirm

You can confirm that your videos were added by clicking on the videos tab and searching for the ones you've just added.

![videos](http://i.imgur.com/MHiAOmb.png)