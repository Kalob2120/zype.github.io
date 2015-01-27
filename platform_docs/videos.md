---
layout: platform
title: Zype Developer Portal | Platform Docs
permalink: /platform_docs/videos/
---
##All About Videos
The Zype Platform is feature rich, so we want to provide you with a place to learn more about it.
Below are a bunch of short tutorials (with pictures!) to help you with videos.

<div style="width: 100%;">
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#1">
    Learn About Dynamic Player Technology (DPT)</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#2">
    Monitoring Your Views</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#3">
    Related Playlists</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#4">
    Adding Videos from a YouTube Channel to the Zype Platform</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
  <a href="#5">
  Adding YouTube Videos from a URL</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#6">
    Adding Your Crunchyroll Videos to Zype</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#7">
    Uploading Videos to Zype Using Our Ruby Gem</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#8">
    Walkthrough of the Zype API with a Sample Rails App</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#9">
    Embedding a Player on Your Site</a>
  </div>
  <div style="margin: 20px;"><span class="fa fa-file-text" style="margin-right: 4px;"></span>
    <a href="#10">
    Search Filters on the Zype Platform</a>
  </div>
</div>

<hr id="1">

## Learn About Dynamic Player Technology (DPT)
Zype’s DPT allows you to create player rules based on geography and device.
For example, you could declare that end users will receive the Hulu Player if he
or she is accessing your video via desktop in the United States or the Zype Player
if he or she is accessing your video via desktop in Australia.

### What you need to start

You will need to have a video collection on the Zype Platform from the video sources
that you want to create player rules for.

1\. Make sure you have imported your videos into your [video catalogue](https://admin.zype.com/video_imports)
on the Zype Platform.

![video imports](http://i.imgur.com/t3aczbs.png)

### What you need to do in the Zype Platform

1\. Visit the [Player Rule Page](https://admin.zype.com/player_rules) and click on New Player Rule

![player rules](http://i.imgur.com/qDK0aoL.png)

2\. Complete the Player Rules Form. You will need to know the countries and devices you want for your rule.
Based on countries and devices, you will be given player options that can be served to the end user.

![player rule form](http://i.imgur.com/nxcYd0K.png)

### Using the Player API

1\. Once you have set up your video catalogue in the Zype Platform and you have created your player rules, you are ready to use the Zype Player API!

2\. You can find your player key and api key using the [Zype Platform](https://admin.zype.com/site/api)

![site keys](http://i.imgur.com/V7UoP3i.png?1)

3a\. To make the API call to get the appropriate player
{% highlight ruby %}
GET http://api.zype.com/videos/{video_id}/player/?api_key={api_key}&player_key={player_key}
{% endhighlight %}

3b\. To use the [Zype Ruby Gem](https://github.com/edla/zype-cli) to get the appropriate player
{% highlight ruby %}
@zype_cli = Zype::Client.new
@video = @zype_cli.videos.find(params[:video_id])
@player = @video.player(player_key: params[:player_key])
{% endhighlight %}

*Check our [previous post](http://dev.zype.com/posts/2014/10/10/adding-zype-to-rails/)
on how to set up your Rails App with the Zype Gem!*

<hr id="2">

## Monitoring Your Views
In a previous post, we covered how to use Zype’s Dynamic Player Technology (DPT).
In this post, we'll be covering how to use the DPT logs to see what requests are being made for your video content.
For example, let's say you've uploaded a batch of new videos and after the first 30 days, you'd like to get an idea
of who's viewing your content and what times of the day are most popular for viewing.

### Where can I find my logs?

After you've uploaded some video content to the Zype platform, log in through the [admin portal](http://admin.zype.com/)
and navigate to the logs section under the settings dropdown menu. In this post, we'll cover the request logs,
so feel free to click on that link once you see the logs menu.  

![dpt logs navigation](http://i.imgur.com/cxELdn1.png)

### What type of information can I see in my request logs?

The request logs screen shows you lots of information about the requests made to view your videos.
Here are the most pertinent pieces of information:

Data | Description
---- | -----------
Video	| The video that was requested
IP Address | The IP address of the requester
Country | The country the request was made from
Device	| The device the request was made from
Player	| The player that served the video
Provider | The provider of the content
Revenue Model	| The revenue model of the viewer
Status	| The status of the request
Created | The date and time the request was created

![dpt logs](http://i.imgur.com/AULsF7q.png)

### How can I search the request logs data?

The request logs screen gives you a snapshot of the most recent requests by default.

Sorting the request logs is easy: use the four drop down menus to select your search parameters
and then click on the search button.


![searching logs](http://i.imgur.com/l2N4Kql.png)


*Check our [previous post](http://dev.zype.com/posts/2014/10/10/adding-zype-to-rails/)
on how to set up your Rails App with the Zype Gem!*

<hr id="3">

## Related Playlists
Let's say you've already got some video content on your zype destination site, but now you'd like to recommend
additional content based on what your users are watching. The solution we've implemented is called related videos.
In this post, we'll be covering how to create a playlist of related videos that are recommended to a viewer
based on what the video they're watching. Here's an example of the finished product:

![related playlist](http://i.imgur.com/wPXZ772.png)

*The related videos section is automatically created for each video on your site, but if you'd like to be more
specific about which videos are displayed there, follow along as we set up a playlist of related videos.*

### How do I set up a playlist of related videos?

Setting up the playlist can be done from the [admin portal](http://admin.zype.com/). Navigate to the playlist
section on the sidebar and and click "New Playlist". Follow through the menu and create a playlist (make sure it's active!).

![playlist navigation](http://i.imgur.com/oXi3Dlg.png)

### How can I choose which videos are shown in the playlist?

This is an easy one. Use the "Add Videos" button to select which videos will appear under the related videos section.

![add videos navigation](http://i.imgur.com/hMAkhgQ.png)

### How can I choose which videos display the playlist?

Choosing the videos that will have your playlist displayed is done through the playlist edit screen. You can get there
quickly by clicking on the name of your playlist here:

![edit your playlist](http://i.imgur.com/XSvwXVR.png)

Use our multiselector to search for the videos you want and click on them to move them into selected videos.
Click "Save Changes" when you're done.

![choose related videos](http://i.imgur.com/WRtRv8m.png)

### Let's confirm

You should take a second and make sure everything's going according to plan. Go to your site and view a video
that you added to selected videos in the previous step. Below the video, under the section "Related Videos",
you should see the playlist you just created and the first few videos you added. You can also update any of your
current playlists to act as a playlist of related videos by following these same steps.


*Check our [previous post](http://dev.zype.com/posts/2014/10/10/adding-zype-to-rails/)
on how to set up your Rails App with the Zype Gem!*

<hr id="4">

## Adding Videos from a YouTube Channel to the Zype Platform
We simplified the process of searching for and importing a YouTube Channel into the Zype Platform.
Before, you had to manually go to YouTube and find your Channel ID. This was a cumbersome
process. Now you can search for a YouTube Channel from the Zype Platform and we will get the Channel ID for you.

**Step 1:**

Go to Video Sources and click on the YouTube icon.

![click youtube](http://i.imgur.com/xJoXbpp.png)

**Step 2:**

Enter a name for your YouTube Video Source (something to help you remember it!) and click the
Search YouTube Channels button

![search youtube channels](http://i.imgur.com/Ly24GBg.png)

**Step 3:**

Enter the channel name that you are searching for and click Search. You will be
given a list of YouTube Channels that match your search criteria. Click the Select Channel
button for the YouTube Channel that you want to add.

![click select channel](http://i.imgur.com/hpAfMu8.png)

**Step 4:**

This will prepopulate the Channel ID for you. All you need to do is click Save Changes
and the Zype Platform will start to import all of the videos from the channel that you selected!

![click submit](http://i.imgur.com/fszuPQu.png)

**Step 5:**

Your imported videos are in your import videos page. You can add videos to your catalogue
from there.

![import videos](http://i.imgur.com/ZKliLxG.png)

<hr id="5">

## Adding YouTube Video from a URL
We're happy to announce that the [Zype Platform](http://admin.zype.com) now grants you the power to import videos from YouTube simply by copying an pasting a YouTube link into the platform.

Check out the [Video Imports Screen](http://admin.zype.com/video_imports) and click on the "Add a YouTube Video Import" button to get started.


![navigate to form](http://i.imgur.com/4lSzNBt.png)


The next step is to copy a URL from YouTube that shows the video you want to add.


![copy url](http://i.imgur.com/QdHp2nM.png)


Paste the URL into the field on this page and click "Add Video Import".


![paste url](http://i.imgur.com/jtREFxL.png)


If everything went according to plan, you should see the video imports screen again, with a new import from the link you provided. If you're interested in grabbing a bunch of videos from YouTube, you may want to follow our guides under [Adding Videos.](http://dev.zype.com/platform_docs/adding_videos/)

<hr id="6">

## Adding Your Crunchyroll Videos to Zype
We know you have a lot of video content and we know that you want it all to be available to your viewers through the Zype Platform. That's why we're proud to announce that you can now use [Crunchyroll](http://www.crunchyroll.com/) as a video source for videos on the Zype Platform!

As part of the announcement, we want to walk you through the setup involved and get you up to speed. If you've added videos to the Zype Platform using video sources in the past, the will look very familiar.



### Navigating to the Crunchyroll Video Source form

First, let's login to the [Zype Platform](https://admin.zype.com/) and go to [Video Sources](https://admin.zype.com/video_sources). Now click on the Crunchyroll icon.

![click crunchyroll](http://i.imgur.com/oSJebB6.png)



### Adding your affiliate code

Enter a name for your Crunchyroll Video Source (something you'll remember!) and your Crunchyroll Affiliate code (this is provided to you by Crunchyroll when you become an affiliate.)

![add name and affiliate code](http://i.imgur.com/tPG2uZv.png)



### Importing your videos

Now sit back while we go get all of your Crunchyroll videos and add them to the Zype Platform as video imports.
Once we've imported all of your videos you will find them under the [Video Imports](https://admin.zype.com/video_imports) tab. The last step is to create new videos from the imports or add the video imports to videos you already have on the Zype Platform.

![video imports](http://i.imgur.com/tjEUtTW.png)



### Confirm

You can confirm that your videos were added by clicking on the videos tab and searching for the ones you've just added.

![videos](http://i.imgur.com/1JDkFYZ.png)

<hr id="7">

## Uploading Videos to Zype Using Our Ruby Gem
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

![video imports](http://i.imgur.com/tjEUtTW.png)

### Confirm

You can confirm that your videos were added by clicking on the videos tab and searching for the ones you've just added.

![videos](http://i.imgur.com/1JDkFYZ.png)

<hr id="8">

## Walkthrough of the Zype API with a Sample Rails App
We want to make the Zype Platform accessible to as many types of developers as possible. To do this,
we have provided [API documentation](http://dev.zype.com/api_docs/intro/) and are happy
to <a href='mailto:contact@zypemedia.com'>talk with you</a> about creating a turnkey app.

As a developer, I always like to learn by example, so we have created
a template Rails app to show you what you can do with the Zype Platform using our Ruby Gem and also provide you with a starter template if you want to build off of it for your own web app.

We intentionally kept the styling simple and used [Bootstrap](http://getbootstrap.com/) if
you would like to use this example as a foundation to your Rails app.
Feel free to clone the repo [here](https://github.com/zype/zype-rails). You will
need your Zype API and Player Keys from the Zype Platform. The README has directions
to how you can find your keys.

*The Zype Rails Sample App has the following pages and features.*

**Home Page**

The homepage includes all of your playlists, a link in the header to view all videos,
and a search box to search for a specific video. The Playlists can be configured
in the Zype Platform and can be fetched via the Ruby Gem.

![homepage](http://i.imgur.com/XdD1n7n.png)

**Playlist Page**

You can click on any playlist to view all the videos that belong to that playlist. You can sort
the videos based on release date, name, or popularity. Also note that there are Zype Videos
and YouTube videos in the same player. The Zype Platform and Zype API allows you to
seamlessly combine the two.

![playlist page](http://i.imgur.com/uDlDPcK.png)


**Browse all Videos**

The browse all videos uses the Ruby Gem to query the Zype API to get all the videos.
When you hover over a video, you will see the description. Feel free to read the [Video API Documentation](http://dev.zype.com/api_docs/videos/) to see what other information
gtes returned when you query for the videos.

![browse videos](http://i.imgur.com/ys7ZfD3.png)

**Video Page**

When you click on a video's thumbnail, you get directed to the video's page. The video's page
contains the title, description, and video player. The Zype API will deliver the appropriate
player based on where the video source comes from and what Player Rules you set.

![video page](http://i.imgur.com/EjY7wlU.png)

Have questions about implementing our sample Rails app or want to see examples of
other features or in other languages? Feel free to comment below!

<hr id="9">

## Embedding a Player on Your Site
The Zype Platform allows you to manage all of your video content in one place and
then deliver your video content across any platform or device. In this tutorial, I
will map out how to embed a video uploaded to the Zype Platform on any webpage.

**Step 1**

Navigate to your video's page and click on the Embed Code tab.

![Go to Embed Code](http://i.imgur.com/4LcF8Lf.png)


**Step 2**

Copy the embed code.

![Copy Embed Code](http://i.imgur.com/jvHwsnU.png)

**Step 3**

You will need to place the div with the id 'zype_player' where you want your player
to be located on your page.

Currently, you can pass in autoplay, player_key, and subscription_id params.
The player_key is required and can be found in Settings > API. Autoplay and subscription_id
are optional.

{% highlight html %}

<div id='zype_player'></div>
<script id='zype_player_js' src='https://api.zype.com/embed/{video_id}.js?autoplay={boolean}&player_key={player_key}&subscription_id={subscription_id}' type='text/javascript'></script>

{% endhighlight %}

<hr id="10">

## Search Filters on the Zype Platform
If you've been busy adding video content to the [Zype Platform](http://admin.zype.com) and creating playlists, you might be at the point where you've got a few pages of each. To help you better manage your content, we've added a set of filters to the videos and playlists pages:

![video filtering](http://i.imgur.com/BOCwSVG.png)


![playlist filtering](http://i.imgur.com/CVg7VSJ.png)


The filter buttons let you select as many parameters for your search as you'd like. Each button has a dropdown you can use to select a value to search by. The default search options are the categories you've created for your site and "Active" (whether or not the video is marked as active). You can create and manage your categories [here.](https://admin.zype.com/categories)

Once you've selected all of the filters you want to use, click the search button to see the results.

You can search by entering a search term, using the filters or both!

If the filter buttons are greyed out, that's because you don't have any videos or playlists yet.

Check out our previous blog post on [defining categories and playlists](http://dev.zype.com/posts/2014/12/04/defining-categories-and-playlists/), if you have questions about getting started.
