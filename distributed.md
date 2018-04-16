# Decentralised content

As Tim Berners-Lee addresses the problem of content ownership

> A well-documented frustration with Social Network Sites (SNS's) is, in 2009, the fact that each site stores the user's data in a silo.
> The user is not in control of his or her data.
> There are often APIs, but each SNS typically has different types of data and therefore different APIs

Tim tackles this problem with a [Distributed Application Architecture](https://www.w3.org/DesignIssues/CloudStorage.html) which seperates the application from the storage. A user might have a blog, twitter account, a personal website and a an account on an instant messaging platform. Using Tim's Linked Data RDF description as a common interface all this content can be read and brought together under one interface. This has been happening for a long time already with RSS/Atom feeds for content syndication from Blogs.

There are two things missing from RSS that would need to be added

1. A description of possible interactions with the third party content.
2. Per-reader encrption to a per-reader, private URL.

The frist can be handled by [RSS Modules](http://web.resource.org/rss/1.0/modules/) which allows RSS to be extended for this use case. The second is a simple extension by the content provider which will provide a custom URL to each friend encrypted with that friends public key. The latter is straight forward while the former requires some explanation...

## RSS Interactons

Why extend RSS? Some motivating examples:

- Friend A publishes a new blog post...
  - Friend B's social portal reads and wants to provide an interface to post a comment the post.
  - Friend C wants to "like" Friend A's post.
  - Friend D wants to reply to Friend B's comment.

Here Friend A's blog should provide a description of all the ways that the RSS feed consumer can interact with the content published. Follwing linked data princiles

1. each friend would pubish their _comment_ or _like_ somewhere they control
2. then notify Friend A's blog of the related content via Friend A's blogs provided (in the RSS) interaction URL.