# Delete Facebook

## Requirements

Existing distributed tech has failed to be a viable option for FB as its always too complicated for the end user. FB has defined the maximum difficulty that the end user experience can take and it also provides a good starting point to work from.

[Wired have systematically listed all the functionality of FB](https://www.wired.com/story/facebook-alternatives/) and alternatives. This is a great starting point to determine what is needed.

As a User I want...

- Single Sign-up - signup in one process.
- Find friends and add them to my social network.
- Single new feed - read all the going-ons in my social network.
- Single interface, Many services - single, familiar interface to interact with all the different types of media.
- Share/re-post items i see in my feed to everyone/friends.
- Like, Comment on, etc items i see in my feed.
- I want my data to private/secure if i choose so.

## Where existing efforts went wrong

No existing standard/technology has been successful to date (evidently). This is, i believe due to two factors

1. Each proposes to reinvent content publishing on the internet (e.g. Pods in [Project Solid](https://blog.p2pfoundation.net/solid-can-web-re-decentralised/2016/04/07) type frameworks) instead of leveraging what is already there.
2. To fight the momentum that Facebook already has would require a mass exodus which would require a special event e.g. FB leaking data.

## RDF

RDF has a whole echo system of standard that already address social networks but few have been adopted.

RSS has been the most successful to data then this is the basic building block of a distributed social network feed. This needs to be extended slightly to describe how one can interact with the content (Verb URLs?) and what data these interactions expect to receive.

This also opens up the problem of dealing with SPAM which can be mitigated if encryption is used to send temporary auth keys. Also, only "friends" might be allowed to comment on private content. Public content is still need to deal with SPAM.

# Linked Data, privacy and digital legals

Linked data comes into play when deciding where to store the content e.g.

1. Person A creates a private blog post.
2. Person B, friend only of Person A, adds a private comment to the blog post.
3. Person C, also friend only of Person A, wants to view the blog post and associated comments. Person C is not a firend of Person B.

In this situation there are two ways to go:
 
1. Person C can't see Person B's comment. This closes down closed group discssions. Mutual friends of A and B will still be able to see everything.
2. Person B grants permisson for A to decrypt and re-encrypt B's comment for A's friends only. 

To ensure this doesn't go further, and A's friends repost B's content again, some sort of digital legal contract needs to be created and signed but each party that recives the private content. This is required for all private content as once it is decrypted it can be reposted anywhere. Digial signing can be handled via somesort of blockchain ledger.


## Technology/Standards that might help

- [dokieli](https://github.com/linkeddata/dokieli) is a decentralised article authoring, annotation, and social notification tool which works from Web browsers. It is built with the following principles in mind: freedom of expression, decentralisation, interoperability.
- [FOAF Search Engine](http://www.foaf-search.net/)
- [BuddyPress](https://wordpress.org/plugins/buddypress/) [Wordpress Plugin] Enable registered members to create profiles, have private conversations, make connections, create & interact in groups, and much more. Truly a social network in a box, BuddyPress helps you more easily build a home for your company, school, sports team, or other niche community.

## Proposal to leverage existing Blogging infrastructure

All publishing platforms need to:

1. Provide an (extended) RSS feed of the content stream.
2. API for creation, posting content, any other interactions related to content.
3. Register and track followers of the content stream.
4. (phase 2) Accept and comply with digital-legal certificate about re-sharing friends private content.

The first is READ, the second if WRITE and the third (and forth) is ACCESS control.

Publishing platforms can be blogs, photo|video|audio sharing sites or whatever the future might bring. The RSS just has to provide a steam of event items in RDF.

### Extending RSS for interactions

RSS is already widely accepted and supported. Its integrated with nearly all publishing systems and is almost the definition of a news publishing system.

The flow of content on social media can already be easily emulated by RSS feed readers. The only extension to this is the ability to

- **Interact** with the streaming items directly i.e. comment, like, edit etc each being medium specific.
- For the streamer to create **private streams** for individuals or groups of individuals. Public access is already the default case.

In interaction interface need to be extensible so that it can adapt to what ever types of interactions the publishing platform supports and possible future applications. RSS modules provides a way to do this, all that is needed is a standard to do so.

This standard needs to define:

- how to provide a list of possible interactons
    - what they are called (VERBS?)
    - an endpoint for those interactions + HTTP action type i.e. GET, POST, PUT etc
- what data those endpoints require, format, required or optional.
- ?how to render an interface for those interactions?

### Extending Blogs i.e. Wordpress

Existing blogging systems such as Wordpress already have all the infrastructure required to handle the volume of data for a social network the size of Facebook.

To allow a third party Social Network Interface (SNI) to use a WP site as a publishing node the SNI needs to be able to:

- Create a new account and provide credentials e.g. create a new blog via <wordpress.com> or host one privately.
- publish content to the account using the credentials e.g. WP has an API
- track/register reader accounts with their associated public key (i.e. PGP public key) e.g. WP blogs allows multipule user registrations and access control to content based on passwords. 

### Private content

Each registered user on the SNI has a public cryptographic key associated with it. A personal RSS feed is created for each based on what the content owner chooses to show them (access control on a per published item level) and that they themselves desire to read (i.e. filtering by subject, tag etc). This RSS feed is encrypted with their public key as is each private item in the feed that they have access to. 


---

The content of this site is licensed under the [Creative Commons Attribution 3.0 Unported License](https://creativecommons.org/licenses/by/4.0/)


*[RSS]: Rich Site Summary; RDF Site Summary
*[API]: application programming interface
*[WP]: Wordpress
*[RDF]: Resource Description Framework
*[SNI]: Social Network Interface
*[PGP]: Pretty Good Privacy, encryption