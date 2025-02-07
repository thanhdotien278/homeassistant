If you find any information on this page useful, feel free to buy me a coffee:

<a href="https://paypal.me/JimmySchings" target="_blank"><img src="https://github.com/jimz011/homeassistant/blob/master/www/images/old%20images/paypal-donate-button.png" ></a>
<a href="https://www.buymeacoffee.com/w8Jnf6Hit" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>
# Homekit Infused (Lovelace) by Jimz011 October 2019 v 0.13.3 (*updated: 21/10/2019)
My current Home Assistant install (current running version 0.100.2)
This is my current Home Assistant configuration with Lovelace, new users please skip to the introduction.
Existing users can either update or copy new snippets of code.

#### Note: When updating please update from version to version, do NOT skip any version or you will find yourself with a broken lovelace setup. If you fall behind in updates you can find older releases/update guides in the links below. Changes will no longer be shown on this frontpage. Watch this repo or follow me on the [Home Assistant Community Forums](https://community.home-assistant.io/t/homekit-inspired-lovelace-by-jimzz011-may-2019-ha-0-93-x-0-94-x-compatible/117086) if you want to stay up-to-date.

# Click [here](https://www.youtube.com/channel/UCYfcLj3IuQ-1mrnqgCk8f0w) for my YouTube channel
### Click here for the [Full Change Log](https://github.com/jimz011/homeassistant/blob/master/CHANGELOG.md)
### Click here for the [Update Guides](https://github.com/jimz011/homeassistant/tree/master/update-guides)
### Click here for all [Releases](https://github.com/jimz011/homeassistant/releases)

## Introduction
Hello fellow home assistant users, I have started using Home Assistant almost a year ago and I absolutely love it. It is very addictive (as I think many of the people viewing this will know that feeling). Anyways I had done some basic HTML in the early 2000's but that was basically it. So I went into this software and this is what I have got to share. Bare in mind that I am just an amateur hobbyist that has no clue of what he's writing but I just try to read up on the community forums. It is not always as easy as it sounds knowing that Home Assistant changes fast, and I mean really fast. Things written down 2 months ago might already be outdated. So this is the code I came up with messing around with it and it works pretty good :P, ofcourse this is a work in progress and I will try to better the code, make it cleaner and look for details. For now I hope someone can make use of this.

### Screenshots
*Note: Screenshots are outdated, they still reside on the server as reference. My setup has changed a lot do not look at those, look at the videos instead!

#### Video
Video: CLICK ON THE IMAGE TO START VIDEO (*updated 05/08/2019)

[![Watch Video](https://img.youtube.com/vi/Ng0EDltHujY/0.jpg)](https://youtu.be/Ng0EDltHujY)

[![Watch Video](https://img.youtube.com/vi/105sd8tp4dg/0.jpg)](https://youtu.be/105sd8tp4dg)

### How to use

Prerequisites:
- Home Assistant 0.98.x or 0.99.x (note: personal themes are broken since 0.97.x if you want to use themes you will have to set them globally! This means the theme will change for ALL users. It might be my own mistake of having weird css or it might be an error in HA itself. Only time will tell)
- A bunch of custom-cards, see below for links
- Patience
- Some more patience
- A whole lot of more patience
- Have lovelace set in `yaml` mode, !includes and !secrets are NOT supported in storage mode. 
To set lovelace to use the yaml mode put the following line into your `configuration.yaml`:
```
lovelace:
  mode: yaml
```
- Basic knowledge of lovelace (if you do not have this, don't even start)
- Know how to use includes and decluttering-cards/templates (see explanation below)
To use this Lovelace setup I highly recommend it that you only try this on a test environment or have at least basic knowledge of how to use Lovelace and custom cards. If you don't know how to work in Lovelace you could seriously hurt your setup to the point it will no longer render the page until you fix the error.
```
ALWAYS MAKE BACKUPS!!!!!!!!!
```
Make sure you always make a backup of your `ui-lovelace.yaml` file and other files if needed. I can not give guarantees that the setup works for anyone but myself. Everyone has different entities and more or less switches/sensors/camera's etc. If you happen to have a quite similar setup like I have you might get away with just changing the entity ID's but I highly recommend you to only use snippets of the setup and not just blatantly copy the entire thing and complain that it doesn't work. Because trust me, it isn't going to work :D. If you do decide to take the risk and copy everything, then make sure you at least remove ALL of the !secret entries and replace them with values of your own, and if you do not have those values yet, comment them out! Fail to do this and it won't start. Next is making sure you have every custom card setup, do this with HACS, find the link and instructions below. One day I might make a version that is more like a template and will only require changing basic stuff, but that day is far away (if ever). Though recent changes have put this setup in the right direction.

Try to use RAW versions of the text to avoid any kind of wrongful spaces. Remember that I warned you :D!

To make it easier on you if you want to copy it entirely is to first check the following:
- Make sure to either remove or replace ALL `!secret` entries as it won't start if they are undefined. I'd suggest commenting out the lines in lovelace and replacing them with your own config in `configuration.yaml`. For your convenience an example of `secrets.yaml` is provided so you could build from that.
- Make sure you have downloaded all custom-cards with HACS (and/or imported them) before you begin.
- Make sure you download the relevant custom-components if desired
- I have a split config, this means saving things will not be as you are probably used to. Regular files like automation.yaml etc will behave as usual. This means changing anything in these files will require a restart or a soft restart from the UI. Lovelace behaves differently this way. Yes it is easier to manage, but it comes with a major downside. Any changes made in any of the files in lovelace will require you to save `ui-lovelace.yaml` every single time! DON'T FORGET THIS! Even if you don't make any changes to this `ui-lovelace.yaml` and have changed ONLY `main-view.yaml` you will still have to save `ui-lovelace.yaml`. Best way to do this is just to do a save all action in your favorite text editor. Know that some editors do not allow you to save if the file is unchanged (e.g. notepad++). I suggest not using any of those text editors. I would advise you to use Sublime Text Editor as it is lightweight, free, easy on the eyes and makes code look a lot more comprehensible.
- To start I would suggest trying to get a light page working. Why? Well, lights are probably the first smart items you already have, not only that, it will also be the easiest page to setup. To start, in your `ui-lovelace.yaml` file comment out all the views except for `light.yaml`. Edit all the entities to match your own and voila you will have your first page working.
- Uncomment views in `ui-lovelace.yaml` one by one to get the basics working. Navigation links (the ones in the quickmenu and the ones in the main menu will not work until you have uncommented all the views!)
- On some Android devices it won't accept a hold_action when deep_press: true is enabled. Remove these lines from the switch-template.yaml and light-template.yaml. It is only useful for iphone users and will do nothing for Android.
- LEARN how to use decluttering-cards, click on the link below at the addons and read the documentation. My config really has a lot of those and knowing how to use them will save you a lot of time, headache and mostly a lot of duplicate code! This is important, please do not flood me with questions about this card if you haven't read the documentation.
- LEARN how to use popup-cards, click on the link below at the addons and read the documentation. I use popup-cards occasionally on some views and they are not easy or straightforward to setup. If you do not know what you are doing these cards will just never work and you will be presented with the standard more-info window that HA offers out of the box. Any config I have made in these cards will not work until you learn how to use these. My advise is to do this last as they are one of the least important features and 95% of the config will work just fine without these working yet.
- Know how to use !includes, includes can seriously be a pain in the behind when any of the paths are wrong or missing. Lovelace will not load and it will always show you a states-ui view if any of the paths are missing or wrong. I stress out that you will ALWAYS have to make SURE that the paths in your files are correct. e.g. if a file refers to another file with an include, make sure the path exists. Luckily since HA 0.98.x it has become easier to find missing includes as the error handler will now tell you in lovelace.
```
type: vertical-stack
cards:
  - !include lovelace/blank-card.yaml
```
If the path /lovelace/blank-card.yaml does not exist or is incorrect lovelace will not load (no matter if it is the only thing that is wrong). If the file `blank-card.yaml` does not exist it will not load.
I stress this because this will make people cry really hard as there is NO error checker and you will have to go through all the files manually. (The error checker will be available in HA 0.98.x and so this will become easier to troubleshoot in the future)

- I can't stress out more that it is ALWAYS better to build from the ground up instead of copying a setup. I would advise you to copy snippets of the code to incorporate that into your own setup. But if you really want to dive in deep you are free to do so.

## Addons Required
#### You will need HACS to download them for use with this setup (you can use the older custom_updater but I would highly recommend you to use HACS instead https://custom-components.github.io/hacs/installation/manual/). Some of the addons are not available on HACS, however you can import them yourself. Read the HACS docs on how to install non supported plugins/addons!! The links provided here will help you add them quickly. Some addons can not be imported directly because the developer did not put the addon in a folder in the root of the directory. When this happens you can either choose to copy the files from my repo or clone the corresponding repo get the folder you need and upload it to the root of your own github project (it does not matter which repo you use for it as long as it is in the root your repository) You can then import the custom card from your own repo into HACS.

Now lets get into the custom-cards and components you will need (components are optional as they might not apply to you).
Cards:
* [Lovelace-Auto-Entities](https://github.com/thomasloven/lovelace-auto-entities) - Not supported, install Manually - This card does what monster-card does but slightly different. Use it to make entities/cards show up/hide depending on a domains/entities state.
* [Weather-Card-Graph](https://github.com/sgttrs/lovelace-weather-card-chart) - Not supported, install Manually - This card is almost the same as most weather cards for lovelace, however this one has a neat graph (and no colored icons which is in my opinion cleaner).
* [More-Info-Card](https://github.com/thomasloven/lovelace-more-info-card) - Not supported, install Manually - This card will show you the more-info window of an entity as a card. This is used for the weather panel in my setup.
* [Card-Loader](https://github.com/thomasloven/lovelace-card-loader) - Not supported, install Manually - This mod will make sure cards are loaded before they are presented. Without this cards might not load until a refresh of the page.
* [Deep-Press](https://github.com/roflcoopter/deep-press) - Not supported, install Manually - This is a great card for iphone users with 3d touch. Actually it isn't a card it modifies existing cards to support 3d touch. If you have an iphone that supports this I highly recommend you to use this. If you are not using this, remove the `deep_press: true` line from `switch-template.yaml` and `light-template.yaml`.
* [State-Switch](https://github.com/thomasloven/lovelace-state-switch) - Not supported, install Manually - Important if you want to be able to have multiple users to use your interface. My setup is not compatible out of the box without this. If you don't care for multi user you will have to manually remove the custom:state-switch entries.
* [Swipe-Card](https://github.com/bramkragten/custom-ui/tree/master/swipe-card) - Not supported, install the file from my repo! - This is used to display the beautiful animation on the 'popup' cards and being able to swipe/flick through them. This is ESSENTIAL. Note: Swipe-Card has a known issue with swiping on pages with buttons. It would register it as a tap_action while you swipe. To prevent this please download the js from my repo instead of the official one as this has a somewhat fix for that problem. You will need this if you do not want the buttons to be tapped while swiping.
* [Button-Card](https://github.com/custom-cards/button-card) - HACS Supported, install with HACS - The MOST IMPORTANT card of my setup, you will need this!!
* [Lovelace-Card-Mod](https://github.com/thomasloven/lovelace-card-mod) - HACS Supported, install with HACS - Mods all the core cards to use CSS etc. Previously card-modder was used for this purpose.
* [Card-Tools](https://github.com/thomasloven/lovelace-card-tools) - Not supported, install Manually - ESSENTIAL many custom-cards depend on this, including Card-Modder
* [Compact-Custom-Header](https://github.com/maykar/compact-custom-header) - HACS Supported, install with HACS - Not essential, however one of my most favorite cards, it makes swipe navigation possible in lovelace as well as the ability to tweak the header just the way you want! I recommend to install this.
* [Popup-Card](https://github.com/thomasloven/lovelace-popup-card) - Not supported, install Manually - This card is no longer essential, if you had it before you can keep it. This will no longer be used in the future. However it is still used on some pages. Though the pages will load fine without this.
* [Thermostat-Card](https://github.com/ciotlosm/custom-lovelace/tree/master/thermostat-card) - Not supported, install Manually -  You will need to clone this card to your own repository as HACS can't read subfolders on github repo's or find someone that has it.
* [Upcoming-Media-Card](https://github.com/custom-cards/upcoming-media-card) - HACS Supported, install with HACS - Required if you want the upcoming media card. You will require a custom component for Sonarr and Radarr as well. If you do not run something like Kodi/Plex and get the films/series yourself you will have no use for this.
* [Lovelace-Markdown-Mod](https://github.com/thomasloven/lovelace-markdown-mod) - HACS Supported, install with HACS - Mods the core markdown card to be more useful. Previously useful-markdown-card was used for this
* [Vertical-Stack-In-Card](https://github.com/custom-cards/vertical-stack-in-card) - HACS Supported, install with HACS - You do not need this and I would not recommend using it on this setup. I have modified the js to have a transparent background as this card enforces a background. I'd recommend using a regular vertical-stack for this. I only use this for my custom:check-marker-cards
* [Mini-Media-Player](https://github.com/kalkih/mini-media-player) - HACS Supported, install with HACS - Beautiful replacement for the standard media player. I'd recommend this. The border-radius can not be set for iOS with a card-modder card on this. You will have to change the border radius in the js file of the card. Don't know what you are doing? Don't worry you can always redownload the file. Or just leave it as is.
* [Lovelace-Xiaomi-Vacuum-Map-Card](https://github.com/PiotrMachowski/Home-Assistant-Lovelace-Xiaomi-Vacuum-Map-card) - HACS Supported, install with HACS - This is the vacuum map card I use to set up zoned cleaning or make the robot move to a certain location on the map! If you have a vacuum then this is a must and I highly recommend you to download this
* [Calendar-Card](https://github.com/ljmerza/calendar-card) - HACS Supported, install with HACS - This is the card I use to show our calendars. Recommended!
* [Simple-Weather-Card](https://github.com/kalkih/simple-weather-card) - HACS Supported, install with HACS - This is the beautiful minimalistic weather card which is seen on the top of my home screen. I like it a lot as it takes so much less space than most weather cards and it is imo one of the least important data to know. All I need to know is, what is the Temperature and "Is it going to rain?".
* [Lovelace-PostNL](https://github.com/peternijssen/lovelace-postnl) - HACS Supported, install with HACS - Highly recommended if you are a Dutch citizen (all Dutch citizens use this postal service). If you are not Dutch it is no use to install this. Get a card that does fit your needs! (if there is one ofcourse). You will also need to install the Custom Component, you can find this on my repo.
* [Mini-Graph-Card](https://github.com/kalkih/mini-graph-card) - HACS Supported, install with HACS - The best card for making graphs by a long shot! Highly recommended!
* [Light-Entity-Card](https://github.com/ljmerza/light-entity-card) - HACS Supported, install with HACS - A beautiful replacement for a color wheel. Can be used as a card or as seen in my setup (see video) with a popup card.
* [Lovelace-Decluttering-Card](https://github.com/custom-cards/decluttering-card) - HACS Supported, install with HACS -  ESSENTIAL and VERY IMPORTANT. None of the buttons in my config will ever render without this card. All buttons except for the light buttons are based of a single template. No template means no buttons. Do not fail to install this! This card is used as a replacement to YAML anchors which I previously used in my setup. This is way more versatile and better in every way (though anchors have some benefits as well).
* [check-button-card](https://github.com/Gluwc/check-button-card) - Not supported, install Manually - This is the card I use to track how long ago a specific action was done (e.g. how long ago it was when the bathroom was cleaned). They are easy to setup and it is easy to use, however I am not satisfied with the way it looks. It is in my setup right now, but will likely be removed in the future.
* [bar-card](https://github.com/custom-cards/bar-card) - HACS Supported, install with HACS - used in the printer ink levels. I might use this card more often in the future.
* [air-visual-card](https://github.com/dnguyen800/air-visual-card) - HACS Supported, install with HACS - a beautiful air quality card with the current outside temperature. I use this on the widgets and weather views.
* [lovelace-valetudo-map-card](https://github.com/TheLastProject/lovelace-valetudo-map-card) - HACS Supported, install with HACS - the great card that imports livemaps from a rooted xiaomi roborock with valetudo.
* [lovelace-xiaomi-vacuum-card](https://github.com/benct/lovelace-xiaomi-vacuum-card) - HACS Supported, install with HACS - Used only on the widgets page. You don't need this if you don't want this as a widget.

Custom Components:
* [RDW-Sensor](https://github.com/eelcohn/home-assistant-rdw) - Not supported, install Manually - Only useful for Dutch citizens. Used for car license plates, APK and Insurrance tracking.
* [Sonarr-Upcoming-Media](https://github.com/custom-components/sensor.sonarr_upcoming_media) - HACS Supported, install with HACS - Required to use with Upcoming Media Card.
* [Radarr-Upcoming-Media](https://github.com/custom-components/sensor.radarr_upcoming_media) - HACS Supported, install with HACS - Required to use with Upcoming Media Card.
* [XboxOne](https://github.com/hunterjm/hassio-addons/tree/master/xboxone) - Not supported, install Manually - Xbox One Component to control you Xbox one from Home Assistant
* [Lovelace-PostNL](https://github.com/peternijssen/lovelace-postnl) - Not supported, install Manually - You will need this to use with the PostNL lovelace card. Without this component the card is useless! Configuration remains the same as if you would use the official PostNL component. Just download the entire folder from my repo to your custom_components folder.
* [Apple-TV-Fix](https://github.com/chamberlain2007/apple_tv_mrp) - Not supported, install Manually - This is a component that aims to fix the ATV problems that came with tvOS 13. Some functions work, some don't. Use at your own risk. If HA will have this component updated I will remove this again. But for now it suits my needs.

## TO DO (*updated: 30/09/2019)
- Finetuning themes and add new ones ###In Progress
- Switching the swipe-card for standard views with CCH. ###Feature request has been released, so this can go in to production
- Scenes (continue the testing of my automations and where needed change) ###Postponed for later evaluation
- Xiaomi Plantsensor Cards ###Postponed to a future release
- Dog food and water dispenser ###Water dispenser died, waiting on RMA
- Other graphs related to servers/computers etc. ###Prework Done
- Declutter some more cards ###Always in Progress
- Add even more buttons to then menu to get all functions in one place ###Currently in Progress
- And many more, which I can't think of at the moment and trust me it is probably a lot! ###Always in Progress

## Requested Features (all requested features will appear here, I make no promises, but I will try to add these)
- p2000 monitor (for Dutch citizens)
- Fuel prices
- Newsfeed
- Public Transport (for Dutch citizens)
- Flight Information

### Questions?

Please ask any question you have on the Home Assistant community forums.
https://community.home-assistant.io/t/homekit-inspired-lovelace-by-jimzz011-may-2019-ha-0-93-x-0-94-x-compatible/117086

## Thank you

Thank you for taking your time reading all this mess, I hope you have great fun with Home Assistant as I have and I will always try to help people out where I can, but as I said I am only an amateur so do not expect miracles :P.
Anyways have fun and see you next time!

## A very special thanks to
@ciotlosm

@thomasloven

@balloob

@gluwc

@maykar

@robbiet480

@ljmerza

@iantrich

@kalkih

@bramkragten

@peternijssen

@eelcohn

@hunterjm

@jc2k

@kuuji

@romrider

@roflcoopter

@3_14 / @Piotrmachowski

@xMrVizzy

@MarsWarrior

@everyone I forgot to mention

I am really sorry, I have tried to get you all. But also a very big thank you to all of the ones not mentioned here. And ofcourse the Home Assistant community which helped me out a lot.

## Author

Jimz011
