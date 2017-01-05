# About

I'm a software engineer located in Seattle, Washington. I have experience with
web service engineering and mobile application development (primarily iOS).
My education and interests include user experience, algorithms, and machine
learning. In a past life I was [pretty decent at polymer chemistry.](http://www.ncbi.nlm.nih.gov/pubmed/15754386)

# Selected Work

<dl>
  <dt><a href="https://www.ibm.com/cloud-computing/bluemix/">IBM Bluemix</a></dt>
  <dd>
    Private Cloud-as-a-Service, powered by OpenStack. Developed internal and
    customer-facing tooling to enable deployment and management of private and
    hybrid cloud infrastructure including bare metal and virtualized compute
    instances, load-balancing, software-defined networking, block storage, and
    object storage.
  </dd>

  <dt><a href="http://local.amazon.com">Amazon Local</a></dt>
  <dd>
    Discount local services from the world's most trusted company. Built mobile
    clients and service infrastructure servicing millions of customers and merchants.
  </dd>

  <dt><a href="http://vocalocity.com">Vocalocity</a></dt>
  <dd>
    Simple VoIP telephony for small businesses. [Acquired in Oct 2013](http://techoperators.com/portfolio/vocalocity-acquired-vonage-vg)
    by [Vonage](http://www.vonage.com)
  </dd>

  <dt><a href="http://www.dungeonhighwayadventures.com">Dungeon Highway Adventures</a></dt>
  <dd>
    Mixed 2D/3D shooter with an 8-bit aesthetic created with [Unity](http://www.unity3d.com)
    for iOS and Android.
  </dd>

  <dt><a href="http://liquidtext.net">LiquidText</a></dt>
  <dd>
    An interface supporting active reading on multitouch displays.
  </dd>

  <dt><a href="http://ballisticpigeon.com/folio">Folio</a></dt>
  <dd>
    A PDF reader for iPad and iPhone.
  </dd>

  <dt><a href="http://til.tense.io">Today I Learned</a></dt>
  <dd>
    Short write-ups of day-to-day engineering and development learning
  </dd>
</dl>

# Writing

{% for post in site.posts %}
* [{{ post.title }}]( {{ post.url }} ) {{ post.date | date_to_long_string }}
{% endfor %}

