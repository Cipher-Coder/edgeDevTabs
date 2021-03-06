[![GitHub license](https://img.shields.io/github/license/Cipher-Coder/devTabs.svg)](https://github.com/Cipher-Coder/devTabs/blob/master/LICENSE.txt) [![Download for Edge](https://img.shields.io/badge/Download-Microsoft-blue)](https://microsoftedge.microsoft.com/addons/detail/mjnididbffjmpdccgmcbdmondlpafkef?hl=en-US)

# Dev Tabs

## Edge, Chrome, & Firefox browser extension for Developers - Replaces your 'New Tab' page

[Download From Microsoft Edge addons](https://microsoftedge.microsoft.com/addons/detail/mjnididbffjmpdccgmcbdmondlpafkef?hl=en-US)

![Screenshot](/src/img/screenshot.png)

### Github Repo's

The [Github](https://www.github.com) repo's, on the right hand side of the page, lists the first 10 repo's in your profile. This makes it easy to quickly access a good portion of your repos.

I used a library called [GithubFeed](https://github.com/samwx/GithubFeed), from 'samwx' to implement this. The library is very well documented however, I did have to alter the code slightly to conform with Chrome's security policies, as well as the CSS so it matched the Dev Tabs page.

Once you open the extension for the first time, click the settings cog in the middle of the page. The first setting is the 'Github Feed'. If you just put your Github Username in the input and save it, when you go back to the main page it will automatically load your Feed on the right hand side of the screen.

Once you save your username, it gets put into local storage and accessed from there. I debated on putting it into the chrome.sync.storage so that it gets sync'd across all instances of chrome/Edge, but ultimately decided to stick with local as it is not really hard to type it in. I also know that I have multiple Github accounts and may want to have one show up for my normal chrome instance and another username for my [Google Chrome Canary](https://www.google.com/chrome/canary/) instance. Just keep this in mind if you ever clear your local storage, you will have to input your usernames again. It is the same for the calendar. In fact all the storage in this extension is stored in local storage.

### Github Calendar

The [Github](https://www.github.com) calendar is integrated with a library from IonicaBizau. The library is [github-calendar.js](https://github.com/IonicaBizau/github-calendar), and can display your github contribution calendar. Very well explained lib, and is responsive. I changed the original styles that came with it to match the basic styles of the Dev Tabs page.

When you first start the extension, look under the weather info at the center of the page and click on the settings cog. On the settings page just click on the 'Github Calendar' selection on the left and fill in your github username. No quotes or anything and click save.

Again, this username is stored in chrome.storage.local. So if you clear your browser, you will have to input it again. This may change in the future. I may ultimately decide to put it in chrome.storage.sync, but for now, this is how it is.

### Time and Date

The time and date is pretty self explanatory. Just a clock with the date. I made it stand out with the color and I was going for a slight glow to it, so when I glance at it, it's easy to see.

### Dev.to

This is hooked up to the [dev.to](https://dev.to) API. It gets the articles from their website and creates a card for each individual article. Once the card is created, it gets appended to the div and the content gets appended to that. I had a bit of trouble getting chrome to not show the broken link image when there was not a url included for the articles image, but I beleve I have it figured out now. In the future, I may add a setting to display your individual feed. But for now, it is just the general article feed.

### Dev.to Twitter

[dev.to](https://dev.to) also has a Chrome extension for Twitter.. [thepracticaldev](https://github.com/thepracticaldev/DevTwitter) is the github repo. It has an MIT license attached to it so I borrowed some of the code. I went ahead and added their content script into the extension. Now, when you log into your [Twitter](https://twitter.com) account, a box on the left hand side of your feed will show up with the days dev.to headlines. It will look something like this:

![Twitter Picture](/src/img/twitter.png)

### Weather

This is just to display your current weather conditions. As I explained in the settings, I set it up to display your local weather. If you go to the settings and click the button to locate yourself, it will hit the HTML geolocation API. Once that is hit, it will take your coordinates, store that value in local storage. Then when you flip back to the main page it will take the coordinates from local storage, and hit the [Open Weather Map API](https://openweathermap.org/api) and display your weather conditions. That is all it does with that info. With that being said, this does not continually track you. It will store those coordinates until you go back to the settings page and hit the button again. So if you move to a different locale and want that weather, you will have to go back to the settings and just hit the button again.

### QR Code Generator

So many times I am in the middle of reading an article or watching a tutorial and I have to stop what I am doing and go do something else. This was the main inspiration behind this tool. I work from home and everyday, at 2:15pm, I have to stop what I am doing and go pick up my kids from school. I have to wait in line for usually around 30 mins, just sitting, with the car off. Now if I am in the middle of reading something, I can click the icon button in the toolbar and copy the url of whatever site I am on and create a QR Code that I can scan with my phone and take with me. Then while waiting to pick the kids up, I can continue to read what ever it was I was working on.

![Screenshot](/src/img/screenshot2.png)

## Location and Tracking

It was important to me that this extension not have any kind of tracking, storing of personal identifiable information, or serve any ads. This page is the first tab you see when you open your browser. It is the tab you will see every time you open a new tab. One of the motivations for making this extension was that I could not find any other new tab page, that I liked, that suited my needs as a new developer, and did not have any ads, or tracked me. I even left off Google analytics. There is nothing in the code that will track you. It is open source. You are welcome to check the code and change it any way you would like, the license is attached.
