---
layout: post
title:  "Deploying Shiny apps with shinyapps.io"
date:   2014-10-11
categories: articles
tags: [data science, R, RStudio, shiny, shinyapps.io]
comments: true
share: true
---

So I've been messing around with Shiny for a year or so now.  It's great tool and getting greater.

**the good:**

* capability to rapidly build an interactive visualization with the full universe of R packages to choose from for the computation engine and visualization options.
* ability to code and house the visualization/app in the same language/place as the code that actually conducts the analysis.
* integrates seamlessly into analyst's workflow.

**the bad:**

* sharing can be hard
* developed by analysts, used by analysts ... and maybe others
* need to download and run R to power app

**the ugly:**

* if your app is ugly, it doesn't have to be! Make it prettier with one of the 951,233,521 R graphics packages out there.

### Sharing Shiny apps 

**Option 1: Rstudio Shiny Server:**  If you have a linux server and the IT chops to configure it, you can set up your very own [Shiny Server](https://github.com/rstudio/shiny-server#shiny-server) to host your whizbang Shiny apps.
We actually set one up at my company, and it is pretty awesome... however I didn't set it up and I don't pay for the server.

**Option 2: Shinyapps.io:** If you're just a mere human, like myself, without a server running in your house to host your app on some domain (which also costs $$), 
[shinyapps.io](http://shiny.rstudio.com/articles/shinyapps.html) is for you!

It's pretty nifty.  You can deploy all your apps to the cloud by interacting soley with R and a little configuration within the shinyapps.io interface in the web browser.  
For free. 

Shinyapps.io is the successor to the Glimmer and Spark hosting services Rstudio experimented around 2012-2013.  I setup a Glimmer account last year (which still works as of now -- October 2014).  You actually interact with Rstudio in the internet browser.  I never established a steady workflow... unsure if I should be developing my apps locally and then SSHing into the Glimmer server and copying the apps there, or developing on the server's file system...

In any case, shinyapps.io makes things even easier.  Simply develop and test your apps locally on your computer, and when you're ready to deploy to the world, you simply run:

{% highlight R %}
	deployApp()
{% endhighlight %}


### Getting started with shinyapps.io

A comprehensive walkthrough can be found [here](http://shiny.rstudio.com/articles/shinyapps.html).  But the gist of it is pretty simple.

First register for an account [here](https://www.shinyapps.io/).

Then run the following R code:

{% highlight R %}
require('devtools')
devtools::install_github('rstudio/shinyapps')
require('shinyapps')
shinyapps::setAccountInfo(name='yourUserNameHere', token='yourTokenHere', secret='yourSecretHere')
{% endhighlight %}

Then navigate to directory of app 

{% highlight R %}
setwd('/Users/whoeverYouAre/yourShinyApps/yourFavoriteApp')
deployApp()
{% endhighlight %}

And voila - you've deployed yourFavoriteApp Shiny App to the world... viewable at the URL something like: https://yourUsersName.shinyapps.io/yourFavoriteApp/

shinyapps.io is still very much a work-in-progress.  For example, It's currently [not possible to delete deployed apps](https://github.com/rstudio/shinyapps/issues/23).  However, for 
free hosting of multiple apps with an easy-to-use R and web interface and unintrusive workflow, it's pretty good start. 

###Proof that it works: 

This is a visualization around the [IPIP-NEO personality test](http://www.personal.psu.edu/j5j/IPIP/).  I generated some fake personalities for some familiar names (if you're a [GoT](http://en.wikipedia.org/wiki/Game_of_Thrones) geek).

Also viewable at the URL: [https://brooksandrew.shinyapps.io/ipipex/](https://brooksandrew.shinyapps.io/ipipex/)

**Update (9/1/2015):** It appears I've been bumping up against my monthly limit of free hours with shinyapps.io, so if the app below is not rendered, that's why.  If you're hosting an app on a website like this, you can change Idle Instance Timeout time in Settings to 5 minutes instead of the default of 15 to conserve some hours.

<iframe src='https://brooksandrew.shinyapps.io/ipipex/' style="border: none; width: 1000px; height: 1000px"></iframe>
