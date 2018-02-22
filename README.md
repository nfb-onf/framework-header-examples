#Front-End Framework
==========

```diff
- IMPORTANT NOTE : The header uses the [hashchange event system](https://developer.mozilla.org/fr/docs/Web/API/WindowEventHandlers/onhashchange) to navigate to the project infos page and grid and make sure the user has those pages in his history.
Please make sure the routing system of your project is not conflicting with the hashchange event system.
```

## Initialization

The header has a dependency on jquery to work. You need to add Jquery to your HTML.
The framework was built with the version 2.2.4 of Jquery.

```html
<script src="https://code.jquery.com/jquery-2.2.4.min.js" integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44=" crossorigin="anonymous"></script>
<script>window.jQuery || document.write('<script src="js/lib/jquery-2.2.4.min.js"><\/script>')</script>
```

After that, you need to call the load_framework.js file on our prod server and initialize it.
The index options that you can pass are described below.

```html
<script src="https://interactive-pip.nfb.ca/static/js/load_framework.js"></script>
<script>
    var indexOptions = {
        currentProjectId: 117,
        base_url: {
            fr: "http://grasslands.nfb.ca/",
            en: "http://laplaine.onf.ca/"
        }
    }
    load_framework.init(indexOptions);
</script>
```

##Css
The header css is loaded via javascript (for environnement testing on our side) but if you want the small flash where the html is not styled when you load the page, you can add to your header the css of the header on our prod server.

```html
<link rel="stylesheet" type="text/css" href="https://interactive-pip.nfb.ca/static/css/header.min.css">
```



## Index options parameters

| Parameter                        | Type          | Description          									|
| -------------                    | ------------- | ------------- |
| currentProjectId **(required)**  | number        | The ID of your project in the interactive framework CMS. This will ensure that it’s your project that is opened when you click on “Get more info” in the header.  |
| base_url                         | object        | This is the url in french and in english of your project. This will ensure that the language toggle works. If your project is only available in one language, just set one property. |
| inverted                         | boolean       | By default the navbar is white (false). If you want to change the navbar to black, add this parameter with the value true. |
| displaySoundToggle               | boolean       | By default, the sound toggle is displayed (true). If there is no sound in your project, you can add this property and set it to false.  |


## Social media share

To make the Twitter and Facebook share button works, you need to ensure that this metadata is provided in your html:

| Metas                        | Description   |
| -------------                | ------------- |
| og:title  				   | The title of the page.                                                                                                                     |
| og:description               | A brief description of the content, usually between 2 and 4 sentences. This will displayed below the title of the post on Facebook.        |
| og:image                     | The URL of the image that appears when someone shares the content to Facebook. See [facebook docs](https://developers.facebook.com/docs/sharing/best-practices#images) for images size.      |
| twitter:description          | A description that concisely summarizes the content as appropriate for presentation within a Tweet. You should not re-use the title as the description or use this field to describe the general services provided by the website. <br /><br />Platform specific behaviors:<br /> * iOS, Android: Not displayed<br /> * Web: Truncated to three lines in timeline and expanded Tweet |

## Fav icon

If your project doesn’t have a custom fav icon, please use this code in your html to use the NFB fav icon and apple-touch-icon.

```html
<link rel="shortcut icon" type="image/ico"  href="https://media1.onf.ca/medias/favicon.ico" />
<link rel="apple-touch-icon" type="image/ico" href="https://media1.onf.ca/medias/apple-touch-icon.png" />
```

## Language of the header

The language of the header is based on the domain. (If "nfb" is in the url, the header will be in english, if "onf" is in the url it will be in french).
If it's not finding any of that in the url the language of the header will be english. If you want to test on local in french you can add _?language=fr_ to your url.

## 404

You can find an example of a 404 page in the repo. You can change the background for an image of your project. Recommanded file size : 2048x1152.

## Google analytic tracking

There is also a file in the repo with example of how to track a **page views** and **events**.

### Page view

```javascript
google_analytics.gaTrack({
	language: "en",
	name: "testing",
	ua_code: "madeup1",
	pageview: "page"
});
```

### Event

```javascript
google_analytics.gaTrack({
	language: "fr",
	name: "testing",
	ua_code: "madeup2",
	event: "auto_begin"
});
```

## Facebook pixel

The pixel base code tracks activity on your website, providing a baseline for measuring specific events. Copy the base code below and paste it between the header tags on every page of your website:

```html
<!-- Facebook Pixel Code -->
<script>
    !function(f,b,e,v,n,t,s)
    {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
    n.callMethod.apply(n,arguments):n.queue.push(arguments)};
    if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
    n.queue=[];t=b.createElement(e);t.async=!0;
    t.src=v;s=b.getElementsByTagName(e)[0];
    s.parentNode.insertBefore(t,s)}(window,document,'script',
    'https://connect.facebook.net/en_US/fbevents.js');

    fbq('init', '1722751167968328');
    fbq('track', 'PageView');
</script>
<noscript>
    <img height="1" width="1"  src="https://www.facebook.com/tr?id=1722751167968328&ev=PageView&noscript=1"/>
</noscript>
<!-- End Facebook Pixel Code -->
```