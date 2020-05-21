# SaveToNotion

## Goal
1. Use a keyword to add a todo block in a Notion page. In my case, I collate everything within one single page called 📥 Inbox, and then I triage them once a day.
2. Use a keyword, or a key combination, to capture the URL and Title of Safari’s current tab, collect an additional note from the user about the URL, and then save it as a bookmark embed in the same Notion page (📥 Inbox, in my case). The note collected from the user gets saved as a ‘caption’ for the bookmark, so that the user can later remember exactly why they chose to save it in the first place.

## History
Since Notion doesn’t have an official API yet, good folks like [ivanistheone][1] and [jamalex][2] have created an unofficial Python 3 client called `notion-py`. It is this CLI client that’s used to make changes in the user’s Notion account.

The only drawback is that the user will need Python 3 in their macOS to be able to run this, and unfortunately, all macOS versions currently ship with v2.x by default.

## Preparation
1. Make sure you have Python 3 installed
	1. Open the Terminal and run the command `python --version`. 
	2. In case the version is below v3.0, here’s the [instructions][3] to install the same. If you don’t wish to install Xcode, it’s enough to just install the [Command Line Tools][4] (Apple ID is needed, but not a dev account)
	3. Make sure Python3 exists in `/usr/bin/python3`. If not, run the command `which python3` in Terminal and get the path. Make sure the same path is included in the two script blocks (marked in green) within the workflow. 
2. Install [notion-py][5] client
3. Set up the workflow variables
	1. After you install the workflow, Alfred will ask you to populate the values for 3 variables. They are called `NotionPageName`, `NotionPageURL` & `NotionToken`.
	2. `NotionPageName`: This is the name of the page where you plan to update the todo and the bookmark. This is just used to show the success notification.
	3. `NotionPageURL`: Go to the page in Notion where you wish to update the data. Click on `Share` at top right, and then the `Copy Link` button on the dropdown. Paste this URL as the value of this variable while installing the workflow.
	4. `NotionToken`
		1. To access non-public pages you need to find out authentication token. This auth token is the value of `NotionToken`.
		2. In Google Chrome: open developer tools (keyboard shortcut: `⌘+⌥+I`), navigate to `Application` tab, look under `Storage \ Cookies` and copy the value of `token_v2` cookie.   
			![][image-1]  

		3. You can do similar things in other browsers.
4. Set up the keywords and keyboard shortcuts of your choice for the actions, and your good to go! 👍🏼 

## Future Enhancements
There are a bunch of ways this workflow can be improved upon. Some of those ideas are:
- User should be able to specify their `python3` path as part of the workflow variable, instead of having to edit it within the workflow blocks.
- User should be able to specify whether they want the popup to include extra note (while saving a Safari bookmark) via workflow variables.
- User should be able to save URLs from all browsers they use, and not just Safari.
- User should be able to include not just a URL and a Todo, but also other blocks like Callout, Video embed, Image embed, Tweet embed, etc.
- Some day, I’d like to build my own web clipper for Safari, by deriving from [this tutorial][6].


[![Workflows](https://img.shields.io/badge/-more%20workflows-0a0a0a.svg?style=flat&colorA=0a0a0a)](https://github.com/learn-anything/alfred-workflows#readme)

[1]:	https://pypi.org/user/ivanistheone/
[2]:	https://pypi.org/user/jamalex/
[3]:	https://installpython3.com/mac/
[4]:	https://developer.apple.com/downloads/
[5]:	https://pypi.org/project/notion/
[6]:	https://www.szj.io/tech/2020/05/04/powerup-safari-notion-extension.html


[image-1]:	https://user-images.githubusercontent.com/27700007/82423122-58bc8600-9a51-11ea-91a9-88b97c898568.png