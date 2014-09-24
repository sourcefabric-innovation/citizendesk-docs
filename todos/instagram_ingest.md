
[Instagram API](http://instagram.com/developer/#)
can be accessed via (official) [Python library](https://github.com/Instagram/python-instagram).

Having an app using Instagram API, it is necessary to have an Instagram user (with *user_id* and *pasword*).
The app (when created) gets its [key set](http://instagram.com/developer/clients/manage/#).
When it is used e.g. for the [sample app](https://github.com/Instagram/python-instagram/blob/master/sample_app.py) of the Python library,
*client_id* and *client_secret* have to be filled in that smaple app, alike for any common app.

It looks that useful endpoints could be [a search on tags](http://instagram.com/developer/endpoints/tags/#) (elections, etc.),
and [following](http://instagram.com/developer/endpoints/users/#) e.g. colleagues of the newsroom.

Regarding the Flask framework, there is [an example](http://blog.pamelafox.org/2012/04/using-instagram-real-time-api-from.html) of Instagram API usage together with Flask.

There are other examples of general use of Instagram API in Python, see e.g.
[SciKit Image](http://nbviewer.ipython.org/github/katychuang/Pyladies-ImageAnalysis/blob/master/Instagram%20Image%20Analysis.ipynb),
[a bot](http://codereview.stackexchange.com/questions/58804/my-second-python-script-an-instagram-bot).

