Add To Evernote
===============

A PHP script to add a web page to Evernote for offline reading from anywhere that has Pocket integration.

![Before and after](http://www.diturner.co.uk/downloads/github.jpg)


##Requirements

To use this script you will need the following:

- An [IFTTT account](http://ifttt.com)
- A [Pocket account](http://getpocket.com)
- Some hosting that runs PHP


##Setting up


###Install the Add to EN script

Upload the Add to EN script to your hosting, you will need to add your Evernote email address and the project you want pages to be sent to in the _settings.php_ file. Also, you should change the $salt value to something random since this will be used to prevent other people sending junk to your Evernote account.

Next, download the [Emogrifier PHP script](http://www.pelagodesign.com/sidecar/emogrifier/) and put _emogrifier.php_ in the same folder as _add_to_en.php_. Emogrifier is a script that is more often used when building email newsletters as most email clients like their CSS inline. Evernote also likes its CSS inline, so this script takes the CSS from css.php and applies it to the page content.

###Setup the IFTTT recipe

If you haven't already done so you need to active your Pocket account in IFTTT. 

Then, follow the instructions to enable [IFTTT Webhook](https://github.com/captn3m0/ifttt-webhook) as the WordPress channel in your IFTTT account.

Next, go to the __Create__ menu item to add a new recipe. Choose __Pocket -> Any new item__ and then select __WordPress -> Create a post__. In title put the ``{{Title}}`` tag. In the Body field you need to put the URL of your copy of the Add to EN script along with the salt, e.g. ``http://www.yourdomain.com/foldername/add_to_en.php?salt=helloworld``. The Categories field should contain nothing but the {{Url}} tag as this is what is sent along to Readability. Leave the tag field empty.

Unless you want random people adding to your Evernote account it's best to make your recipe private.

###Test it

Go to an app or browser that has an add to Pocket feature, add something, you should see it pop up into your Evernote project folder. (Note that IFTTT can take 15 minutes to run your script, I'm finding it very often runs faster though.)


##Browser Bookmarklet

If you want to skip the IFTTT/Pocket accounts then you can use this browser bookmarklet:

    javascript:(function(){window.open('http://www.yourdomain.com/foldername/add_to_en.php?salt=helloworld&url='+location.href,'AddToEn','status=no,directories=no,location=no,resizable=no,menubar=no,width=50,height=50,toolbar=no');})();

Remember to update the URL and salt values.
