---
layout: galleryItem
author: <a href="https://github.com/tsvenbla">tsvenbla</a>
title: SQL Server Updates to JIRA Issues
synopsis: This script will create JIRA issues from an RSS feed
type: Working Script
modules:
  - JiraPS
---
### Brief summary

This script will poll an RSS feed containing SQL Server Updates and create issues in JIRA off the feed entry titles.

### Description

I created this script because I was sick of having to manually create a JIRA issue every time there was a SQL Server update/patch release.
This script will take care of all that, if you don't mind a few non-patch issues being created (like SCOM management packs). This could easily be sifted away with content parsing.

This script will do these things, in order:

1. Establish a connection with your company JIRA.
2. Fetch an RSS feed (in my script, the https://blogs.msdn.microsoft.com/sqlreleaseservices/feed/).
3. For each feed item in the feed:
    1. Extract useable information, like the feed item title, publishing date and link.
    2. Check whether there already exists a JIRA issue with the same title/summary as the feed title.
    3. If not, create the issue with a certain set of parameters.
    4. Repeat for each feed item in the feed.
4. Done!

![ScreenShot](screenshots/SQLBacklog.PNG)

### Code

{% gist tsvenbla/1716a662b21ee9574b1bc78ea8efbf15 %}
