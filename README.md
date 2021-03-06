        __ )          |    |    |                     |
        __ \    _` |  __|  __|  |   _ \  __ \    _ \  __|
        |   |  (   |  |    |    |   __/  |   |   __/  |
       ____/  \__,_| \__| \__| _| \___| _|  _| \___| \__|

    A Ruby library for the Battle.net Community Platform API

[![Build Status](https://secure.travis-ci.org/BinaryMuse/battlenet.png)](http://travis-ci.org/BinaryMuse/battlenet)

Battlenet is a Ruby library that exposes Blizzard's [Community Platform API](http://us.battle.net/wow/en/forum/topic/2369881371).

Installing
==========

Battlenet is available as a Ruby gem. Install it via

    [sudo] gem install battlenet

Use
===

Simply create an instance of `Battlenet`, passing in an optional region as a symbol (defaulting to US), and then optionally a public and private key (for app authorization).

Default options:

    api = Battlenet.new

Specifying a region:

    api = Battlenet.new :eu

Specifying a public and private key:

    api = Battlenet.new :us, 'public', 'private'

Battlenet is backed by the excellent [HTTParty gem](https://github.com/jnunemaker/httparty), which means you can make get requests very simply.

    api.get '/item/12784'

Battlenet also provides modules for each section of the API, providing easy access to the resources.

    api.item '12784'
    api.character 'Nazjatar', 'Cyaga', :fields => "stats,talents,quests"

Configuring
===========

Failing Silently
----------------

By default, if Battlenet receives a non-200 response from the Battle.net API, it will throw an exception. You can turn this behavior off via the `fail_silently` attribute:

    Battlenet.fail_silently = true

Localization
------------

The Battle.net API supports localization via a query string parameter. Battlenet can transparently handle setting this parameter for you on every request. Just set the `locale` attribute:

    Battlenet.locale = "en_GB"

Please note that each region only supports certain locales.

Battle.net API Documentation
============================

The documentation for the Battle.net API can be found at http://blizzard.github.com/api-wow-docs/.

What's Missing
==============

The following features are planned but not yet supported:

  * Caching support via Memcached, Redis, etc.
  * If-Last-Modified header support

Contributing
============

If you would like to contribute to the project, please feel free to do so. Just fork the project, commit your changes (preferably to a new branch), and then send me a pull request via GitHub. Be sure to add tests for your feature or fix.

Please do not change the contents of the `VERSION` file, or if you do, do so in a separate commit so that I can cherry-pick around it.

License
=======

Battlenet is released under the MIT license.

    Copyright (c) 2011 Brandon Tilley

    Permission is hereby granted, free of charge, to any person
    obtaining a copy of this software and associated documentation
    files (the "Software"), to deal in the Software without
    restriction, including without limitation the rights to use,
    copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the
    Software is furnished to do so, subject to the following
    conditions:

    The above copyright notice and this permission notice shall be
    included in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
    EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
    OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
    NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
    HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
    WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
    FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
    OTHER DEALINGS IN THE SOFTWARE.
