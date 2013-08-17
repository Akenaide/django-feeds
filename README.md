django-feeds
============

Overview
========

Django feeds is a simple RSS & Atom feed scraper with a couple of extra features to make your news reading & listening habits simpler.  Feedparser is used to gather the entry data from the feeds. NLTK is used in conjunction with functions derived from Jonathon Vogel's [summarize.py][summarize] script.  Currently, the text-to-speech functionality only support OS X's built-in `say` command.

When available, the Feed's `etag` or `last_modified` attributes are used to reduce bandwidth consumption when refreshing news feeds.  To see benefit from this feature, however, support must be enabled/configured server-side as well.

Planned improvements
====================

* Linux text-to-speech support with Festival
* AlchemyAPI integration

Requirements
============

* Python 2.7+ (Tested with 2.7.5)
* Django 1.4+ (Tested with 1.4.5)

Installation
============

Install using `pip`...

    pip install django-feeds

Add `'feeds'` to your `INSTALLED_APPS` setting.

    INSTALLED_APPS = (
        ...
        'feeds',        
    )

Optional: Set the `SUMMARIZE_WORD_COUNT_LIMIT` to limit the length of the content created by the summarizer.

    SUMMARIZE_WORD_COUNT_LIMIT = 500

Setup
=====

Start up the dev server to enter in your feed data.

    python manage.py runserver localhost:8000

In the admin, add a new Feed object for each feed you want scraped.

    localhost:8000/admin/feeds

Usage
=====

After you've created your Feed objects, you don't need the server running anymore.

The first step is to refresh the news feeds, which consists of scraping the feeds for data and then summarizing the URLs and updating the cached content field.

    python manage.py refresh_news_feeds

Once it has begun summarizing entries, you can start having your news read! You don't have to wait for it to completely finish if you open up another console window.

    python manage.py speak_entries

Enjoy!

[summarize]: https://github.com/Rotten194/summarize.py