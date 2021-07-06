---
permalink: /installation
title: Installation
---

# Installation

{% highlight shell %}
$ composer require broadway/broadway
{% endhighlight %}

This will only install the Broadway framework. Based on your infrastructure
you can choose an event store implementation (doctrine/dbal or MongoDB) and a
read model implementation (Elasticsearch or MongoDB).

If you use Symfony you can also install the Broadway Symfony bundle. 

Be sure to check our [demo application](https://github.com/broadway/broadway-demo) as well.

## Further reading

* [A Broadway demo application](https://labs.qandidate.com/blog/2014/12/30/a-broadway-demo-application/)
