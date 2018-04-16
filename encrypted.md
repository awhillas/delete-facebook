# Private content

A social network, from a data perspective, is fundamentally just a list of contacts. It also, optionly provides a profile per user account as well as tracks the profile of each friend.

To create privacy in the social network content needs to be encryted for each friend that it is served to. This requires tracking a public encryption key for each friend as part of their profile and passing this on to each distributed, content provider (i.e blog, wiki etc) node.

The social network portal (SNP), the interface that tracks the distributed content of its users friends, reads the encryted content for each friend and recursivly all the associated linked data content syndicates it. This can then be decrypted by ether:

  - the user's client, on the fly in the browser keeping the private key on the local computer
  - the portal which would require the private key be kept remotely and thus trust betweent the user and the portal needs to be estabilished.