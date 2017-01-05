# About

I'm a software engineer located in Seattle, Washington. I have experience with
web service engineering and mobile application development (primarily iOS).
My education and interests include user experience, algorithms, and machine
learning. In a past life I was [pretty decent at polymer chemistry.](http://www.ncbi.nlm.nih.gov/pubmed/15754386)

# Selected Work

* [IBM Bluemix](https://www.ibm.com/cloud-computing/bluemix/): Private
  Cloud-as-a-Service, powered by OpenStack. Developed internal and
  customer-facing tooling to enable deployment and management of private and
  hybrid cloud infrastructure including bare metal and virtualized compute
  instances, load-balancing, software-defined networking, block storage, and
  object storage.
* [Amazon Local](http://local.amazon.com): Discount local services from the
  world's most trusted company. Built mobile clients and service infrastructure
  servicing millions of customers and merchants.
* [Vocalocity](http://vocalocity.com): Simple VoIP telephony for small businesses.
  [Acquired in Oct 2013](http://techoperators.com/portfolio/vocalocity-acquired-vonage-vg)
  by [Vonage](http://www.vonage.com)
* [Dungeon Highway Adventures](http://www.dungeonhighwayadventures.com): Mixed
  2D/3D shooter with an 8-bit aesthetic created with [Unity](http://www.unity3d.com)
  for iOS and Android.
* [LiquidText](http://liquidtext.net): An interface supporting active reading on
  multitouch displays.
* [Folio](http://ballisticpigeon.com/folio): A PDF reader for iPad and iPhone.
* [Today I Learned](http://til.tense.io): short write-ups of day-to-day
  engineering and development learning

# Writing

{% for post in site.posts %}
* [{{ post.title }}]( {{ post.url }} ) {{ post.date | date_to_long_string }}
{% endfor %}

