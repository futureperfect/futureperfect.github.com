# About

I'm a software engineer located in Seattle, Washington. The bulk of my
experience is with cloud infrastructure and web service engineering.
My education and interests center on algorithms, systems, and machine learning.
In a past life I was [pretty okay at polymer chemistry.](http://www.ncbi.nlm.nih.gov/pubmed/15754386)

# Selected Work

<dl>
  <dt><a href="https://www.ibm.com/cloud/object-storage">IBM Cloud Object Storage</a></dt>
  <dd>
    Public cloud object storage service. Developed tools and infrastructure to
    support critical business goals, particularly external monitoring of service
    reliability and delivering customer audit log support across datacenters.
  </dd>

  <dt><a href="https://www.ibm.com/cloud/private">IBM Bluemix Private Cloud</a></dt>
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
    Simple VoIP telephony for small businesses. <a href="http://techoperators.com/portfolio/vocalocity-acquired-vonage-vg">Acquired in Oct 2013</a>
    by <a href="http://www.vonage.com">Vonage</a>
  </dd>

  <dt><a href="http://www.dungeonhighwayadventures.com">Dungeon Highway Adventures</a></dt>
  <dd>
    Mixed 2D/3D shooter with an 8-bit aesthetic created with <a href="http://www.unity3d.com">Unity</a>
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
</dl>

# Writing

{% for post in site.posts %}
  * [{{ post.title }}]( {{ post.url }} ) {{ post.date | date_to_long_string }}
{% endfor %}

