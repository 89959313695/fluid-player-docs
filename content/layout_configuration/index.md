---
title: "Layout Configuration"
type: homepage
---

There are optional parameters that can be used to customise the Fluid Player. 
None of the options are required but can be tailored to better suit your own design.
Layout controls relate to the functionality and styling of the player itself.
The full list of _layoutControls_ are below:

```javascript
fluidPlayer(
   'my-video',
    {
        layoutControls: {
            primaryColor:           false,
            playButtonShowing:      true,
            playPauseAnimation:     true,
            fillToContainer:        false,
            autoPlay:               false,
            mute:                   false,
            keyboardControl:        true,
            layout:                 'default',
            allowDownload:          false,
            playbackRateEnabled:    false,
            allowTheatre:           true,
            logo: {
                imageUrl:           null,
                position:           'top left',
                clickUrl:           null,
                opacity:            1
            },
            controlBar: {
                autoHide:           true,
                autoHideTimeout:    3,
                animated:           true
            },
            timelinePreview:        {},
            htmlOnPauseBlock: {
                html:               null,
                height:             null,
                width:              null
            },
            playerInitCallback:     (function() {})
        }
    }
);
```

## primaryColor
Primary color affects the following areas of the Fluid Player:

* Play button showing before video play (**Default:** grey)
* Play and pause animations and video toggle (**Default:** grey)
* Video played progress bar (**Default:** white)
* User defined [ad text](#adtext) (**Default:** black)

Changing this parameter will change all the above areas to the color specified.
In the below screenshot we have used the following:

```javascript
fluidPlayer(
   'my-video',
    {
        layoutControls: {
            primaryColor: "#28B8ED"
        }
    }
);
```

<img src="screenshots/primaryColour.png" style="height:400px;margin:auto;display:flex;">
<img src="screenshots/primaryColour2.png" style="height:400px;margin:auto;display:flex;">

## playButtonShowing
By default the play button will show in the middle of the player. To hide the button this option can be set to **false**.
When this option is set to **false** the video controls will show by default.

```javascript
fluidPlayer(
   'my-video',
    {
        layoutControls: {
            playButtonShowing: false // Default true
        }
    }
);
```

## playPauseAnimation
There is a Play / Pause animation that can be disabled using this parameter. By default this parameter is set to **true**

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            playPauseAnimation: false // Default true
        }
    }
);
```

<img src="screenshots/playAnimation.gif" style="height:400px;margin:auto;display:flex;">

## fillToContainer
If the Fluid Player is placed into a container on your page you can use this parameter to fill to the size of that container. 
Set this parameter to **true** to set the width and height to 100%

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            fillToContainer: true // Default true
        }
    }
);
```
 
## autoPlay
By default this parameter is set to **false**. When set to **true** the video will play automatically when the page loads.

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            autoPlay: true // Default false
        }
    }
);
```
 
## mute
Set this parameter to **true** to have the video muted by default.

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            mute: true // Default false
        }
    }
);
```
 
## keyboardControl
The following key commands are usable by **Default:**

* **Space/Enter:** Pause/Play video playback
* **Left/Right arrow:** Go back/forward 5 seconds
* **Home/End:** Go to beginning/end of video
* **Numbers 0-9:** Skip to a particular section of the video (e.g., 5 goes to the video midpoint)
* **Up/Down arrow:** Increase/Decrease volume 5%
* **m key:** Mute/Unmute video volume
* **f key:** Go to Full Screen mode

If you wish to disable these options set _keyboardControl_ to **false**

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            keyboardControl: false // Default true
        }
    }
);
```

## logo
The _logo_ option allows you to show an image overlaid in the corner of the player. There are 4 options that can be set to configure this logo.

* **imageUrl:** The location of the image to show. (**Default:** null)
* **position:** Where on the player the logo will show. (**Default:** 'top left')
* **clickUrl:** If you want the logo to be a link to another page you can set the landing page with this parameter. (**Default:** null)
* **opacity:** This will toggle the opacity styling option of the logo. (**Default:** 1)

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            logo: {
                imageUrl: 'https://www.routetomylogo.com', // Default null
                position: 'top right', // Default 'top left'
                clickUrl: 'https://www.landingpage.com/welcome', // Default null
                opacity:  0.8 // Default 1
            }
        }
    }
);
```

<img src="screenshots/logo.png" style="width:600px;margin:auto;display:flex;">

## controlBar
The control bar will hide when the mouse is inactive after a certain amount of time. 
There are three options for this parameter:

* **autoHide:** Configure whether or not to hide the controls. (**Default:** false)
* **autoHideTimeout:** How long, in seconds, before the controls will hide. (**Default:** 3)
* **animated:** If set to false the controls disappear instantly. True be default, will mean the controls fade out. (**Default:** true)

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            controlBar: {
                autoHide: true, // Default false
                autoHideTimeout: 5, // Default 3
                animated: false // Default true
            }
        }
    }
);
```

## timelinePreview
Thumbnail preview is discussed more [here](../preview_configuration).

Sets the timeline preview, visible when hovering over the progress bar. 
The provided file contains the thumbnail images used for the preview. 
The type sets the format of the file. Currently only the VTT format is supported. 
The timeline preview only works if the default layout is chosen (see above).

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            timelinePreview: {
                file: 'thumbnails.vtt',
                type: 'VTT'
            }
        }
    }
);
```

<img src="screenshots/thumbnails.png" style="width:600px;margin:auto;display:flex;">

## htmlOnPauseBlock
Defined HTML to be displayed in the center of the player when the user pauses the video. Note: Clicking on the HTML area triggers a play event. 
If you don't need that behaviour then add **e.stopPropagation()** to your event. There are three options for this parameter.

* **html:** The HTML to display.
* **height:** The height of the HTML to show. An integer representation of the pixel size.
* **width:** The width of the HTML to show. An integer representation of the pixel size.

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            htmlOnPauseBlock: {
                html: '<b>Paused</b>', // Default null
                height: 50, // Default null
                width: 100 // Default null
            }
        }
    }
);
```

<img src="screenshots/paused.png" style="width:600px;margin:auto;display:flex;">
 
## layout
The default layout is **default**. It provides own skin to the player. 
Another option is **browser**, meaning that the standard video player layout and behaviour, specific for each browser, is used.

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            layout: 'browser' // Default 'default'
        }
    }
);
```

## allowDownload
False by default, this option will allow users to download the video shown in the Fluid Player.

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            allowDownload: true // Default false
        }
    }
);
```

## playbackRateEnabled
Fluid Player allows the users to change the playback rate / speed of the video. By default, this option is disabled. 
To enable this option use the following:

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            playbackRateEnabled: true // Default false
        }
    }
);
```

## allowTheatre
Theatre mode alters the size of the player, showing a full screen width and 75% screen height player instead. 
This overlays whatever is behind the player, but allows the users to scroll through the page as normal. This is enabled by default, but can 

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            allowTheatre: false // Default true
        }
    }
);
```

## playerInitCallback
This callback function can be used to execute custom code when the player in initialised.

```javascript
fluidPlayer(
    'my-video',
    {
        layoutControls: {
            playerInitCallback: (function() { console.log('player loaded!') })
        }
    }
);
```
