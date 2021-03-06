awesomeTab for Firefox
======================

The Idea
--------

When you open a new tab in a browser, you see an empty page. awesomeTab is designed to replace that with a more useful page.

Features
--------

Some useful feature that one might consider displaying on such a new tab page are:

+ Bookmarks similar to what pages are currently open.
+ Pages (unbookmarked but 'frecent' that might be relevant)
+ Consider looking at highlights from last page for reference (this is from the original concept)


Panorama
--------

awesomeTab works much better when used together with Panorama. This is because if you have tabes grouped together, then awesomeTab decides based solely on the currently visible tabs. This makes the results more relevant.

Reading
-------

[Aza Raskin on New Tabs](http://www.azarask.in/blog/post/new-tabs/)
[Firefox 3.1 Original Concept](http://www.azarask.in/blog/post/firefox-31-new-tab-spec/)


Software Design
===============

Design Overview
---------------

awesomeTab is implemented as a restartless addon for Firefox. Version 0.1 runs completely off data already stored and tracked in the browser. In later versions, this might modify Firefox to store more user data inside of Firefox to improve user experience.

Workflow
--------

1. User opens new tab, create an awesomeTab instance.
2. awesomeTab calls tagColelctor which returns [(tag, percent_hosts, from_bookmark)] list
3. awesomeTab calls bookmarkSearcher + tagRank with given data 
4. awesomeTab calls placesSearcher + tagRank2 withthe given data.
5. awesomeTag calls resultMixer with places
6. awesomeTag calls tabBuilder with all the supplied data.
