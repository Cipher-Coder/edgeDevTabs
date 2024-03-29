# Changelog

Any notable changes and version notes will be kept in this file.

## v2.3.0

## Changes

#### Changed Onboarding with added link to settings

- Changed wording and made the warning to setup settings to a link instead of directing them to settings. Referencing this [Issue](https://github.com/Cipher-Coder/chromeExtension/issues/1) from the Chrome version.
- Added a Cache for the Github Graph - Too many requests are being sent. Sometimes a single person is aquiring a new tab > 20 times an hour. Since my self-hosted proxy is hosted on GCP the cost is increasing exponentially. Right now, it is set to cache the data for one hour. However, if this does not bring the cost back down to a managable range I will have to increase the time.
- Deleted the two Bridge JS files. They were not needed.
- Fixed inject.js for Twitter portion. After Twitter UI update the CSS classes were not the same, so it was not triggering the the insertion of the [DEV](https://www.dev.to). Now it works when Twitter UI is set to dark mode.
- Added link to Changelog in the icon popup page.

> No other libs added. backgroundScriptsAPIBridge.js & contentScriptsAPIBridge.js libs were removed. The list of libs is at the end of this changelog.

&nbsp;

## v2.2.5

## Changes

#### DEV API update

- DEV api has either changed or been updated and it was no longer fetching the latest articles and displaying them. The articles displayed were stale.

- Updated the API call to pull the latest 20 articles and display them.

> No other libs added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## 2.2.4

## Changes

### Current Streak was not working

- Fixed the current streak that was still not working.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## 2.2.3

## Changes

### Fixed GitHub Contributiions Graph... again

- GitHub's contributions graph on the public facing website, is an SVG. This is where I get your contributions info from to reconstruct that graph as well as do the math on the streaks and other info. However, they keep changing the SVG and how it is rendered and the classNames used as well as the attributes used to create it. I am using a Library to parse this info and I finally forked it and made appropriate changes so that hopefully this will not happen again.

### Minor improvements

- Moved list of bookmarks over slightly on smaller screens

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## 2.2.2

## Changes

### Fixed github rendering graph... again

- Adjusted for GitHub changing their graph rendering.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## 2.2.1

## Changes

### Cache

- Adjusted cache for GitHub Calendar. Just took it out so when you commit something to GitHub it will show in the graph immediately. If the userbase increase a lot, I may have to re-impliment it. But for now, there are not enough users to have to cache the info.
- Fixed rendering issue again - Guessing GitHub keeps changing how they render their graph

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## 2.2.0

## Changes

### HOTFIX: Github calendar not working

- Github Calendar stopped working. Github changed the way they rendered the graph SVG. Added CSS vars so the days would render the way they should and got the streak back.
- Moved the settings button into the popup menu. Got rid of the extra code for that.
- Added some style to the Popup menu
- Updated DOMPurify again.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.7

## Changes

### DOMPurify

- Upgraded the sanitization lib included. DOMPurify has been upgraded to latest version due to a vulnerability.
- Adjusted CSS on Main page to make it slightly more responsive on smaller screens < 1300px
- Moved the "add single bookmark" button up and side by side with options button so it would work on MacBook Pro - < 1300px screen

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.6

## Changes

#### Minor fixes

- Fixed console error when the Dev API returns `null` for the `cover_image` of an article. Added `if` statement to check for `null` and if so `display:none` on the img field.

- Basic Refactoring

- Added a '-' and '+' switch on 'add single bookmark'. So when user clicks to add a bookmark a '-' will appear signaling to user to click again to get back to original state.

- Fixed chrome.storage.removeItem to just chrome.storage.remove, so when you navigate to the settings page and try to delete all bookmarks saved on the left of the screen... now it actually works.

- Changed the font color of the 'save' button on the place where you add a single bookmark.

- Fixed Dev.to article by-line - problem was: if there was no twitter_username returned with the article object, the entire article was omitted. I fixed it so if there is no twitter_username, it will now display and link to the Dev.to username.

- Refactored and fixed the bookmark input section. [Marked.js](https://marked.js.org) no longer sanitized markdown. I was able to use the DOMpurify library that was being used elsewhere and refactored the code appropriately.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.5

## Changes

#### Minor fixes

- fixed script tags outside body in `index.html` - was throwing error
- Darkened Settings UI slightly to better fit w/Dark Theme of Index Page
- API call to Dev.to going stale not fetching the latest articles. Changed the query to fetch 'top' articles and after testing it for days, it seems to be doing much better.
- Adjusted CSS for the list of Repo's so it no longer shows a scrollbar on smaller screens
- Adjusted style on the buttons in the settings to better match overall style
- Released this extension on Microsoft Edge Chrome Browser

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.4

## Changes

#### Total re-write of github-calendar.js

This release is centered around a complete re-write of the `githubGraph.js` file. I changed from hitting GitHub in general to `https://github.com/users/username/contributions` API and instead of parsing the entire profile and getting just the contribution info this will in turn decrease the downloaded file size and increase loading time for the calendar since it is just the contribution info being loaded. A 20 kb vs 382 kb download difference. I also made sure my proxy was coded into the lib so it did not depend on someone else's free tier from App Engine.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.3

## Changes

#### Fixed the URL Proxy I was hitting

The URL Proxy I was using to hit GitHub (in githubGraph.js) and get commit graph details kept going over its limit and interrupting my service. So I created my own Proxy through Google App Engine and am now hitting that and all is working again.

Also changed className in Twitter inject script for new Twitter UI. They are still changing their UI so this may only work temporarily. I will continue checking the site to keep up on the new classNames.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.2

## Changes

#### Fixed the [DEV](https://dev.to) box from showing up in the central feed when you switch to another page

After changing the [DEV](https://dev.to) box CSS classes, I realized that if you were to click on another page it would put the box in the main feed. The CSS classes selected as a reference in the DOM were reused on the other page forcing the box into a position it should not have been in. I had to be even more specific and add in more of the classes to have more specificity.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.1

## Changes

#### Fixed Twitter portion of extension after Twitter's UI update

Changed all CSS classes in inject.js

- Adjusted all function calls
- Changed all class names to match Twitter's new ones
- Changed Template literals so everything will work

_Still some work to be done on styling - Just wanted to at least get it working_

Ran autoprefixer on all CSS files

#### Sanitize user input for the individual bookmark add

- DOMPurify lib is already being used for the input on the settings page. I made sure the input from the single add bookmark on the main page was sanitized as well.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.1.0

## Changes

#### Added option to change the Unit of Measure on Weather Display

Had a request to add in functionality to change the weather information display to Metric

- Added option in the Weather options to toggle between Imperial Units for the US and Metric Units for other countries.

- Now there is a toggle switch before getting weather location. The default is Imperial but you can toggle it to Metric so you can have the Wind Speed displayed in KPH instead of MPH and the Temperature will be in Celsius.

- This selection is stored in 'chrome.storage.local' with all the other options and is just appended onto the end of the API call to Open Weather Map then it will return the info in that unit of measure. Then the browser will check that selection again prior to display and show either MPH of KPH after wind speed.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.0.8

## Changes

#### Bookmarks bleeding into warning on smaller screens

After looking at the extension loaded on a small laptop I noticed that when the bookmarks options are open, they bleed into the warning about tracking on the bottom of the screen

- Shrunk the margin on Options page to try and keep the Warning about deleting bookmarks from bleeding into the donate portion.

- On smaller screens the warning under Delete Bookmarks was mixed into the paragraph on donating.

- I shrunk the margin as well as shortened the message to warn users about deleting the bookmarks.

\*\* This only affected smaller screens otherwise you would not see any difference

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.0.7

## Changes

#### Style Changes

Minor CSS Style changes

- Changed font size and style on the article and repo descriptions

- Bumped padding on the calendar columns

- Added clear function to bookmark input so it will clear when saved

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.0.5

## Changes

#### Steralization

Mozilla notified me that one of the libs I was using needed steralization or a refactor

- I added the purify.js lib and made sure any and all data was steralized

- Refactored and fixed some of the calls to innerHTML

  - In the refactor, I changed some of the library's calls to innerHTML so it is not a carbon copy of the lib

- Completely removed the Content Security Policy - It was not actually needed

&nbsp;

## v2.0.4

## Changes

#### Updated Permissions

Trying to get the [DEV](https://dev.to) feed to show up next to the [Twitter](https://twitter.com) feed. In an attempt to fix it I had added a blanket access policy using wildcard urls. This asked users for access to all browsing data, which I did not need.

- Removed wildcard access to all websites and narrowed to permission to only DEV

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.0.3

## Changes

#### Updated Permissions

The [DEV](https://dev.to) feed is not showing up when on [Twitter](https://twitter.com)

- Updated permissions to include http://\*/ and https://\*/ - This was causing the DEV news feed on Twitter not to work. Once these permissions were added in, everything worked again.

> No other libs were added or taken away. Only the original library's are being used. The list is at the end of this changelog.

&nbsp;

## v2.0.2

## Firefox Public Release

This is the first version released to the public

---

#### Libraries Used

- [Marked.js](https://cdn.jsdelivr.net/npm/marked/marked.min.js)

  - [Marked.js repo](https://github.com/markedjs/marked)

- [GitHub-calendar.js](https://unpkg.com/github-calendar@latest/dist/github-calendar.min.js)

  - [GitHub-calendar.js repo](https://github.com/IonicaBizau/github-calendar)

- [DOMPurify.js](https://github.com/cure53/DOMPurify)

- [Github-Feed.js](https://github.com/samwx/GithubFeed)
