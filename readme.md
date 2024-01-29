# p2p killerapp

my search for the perfect peer to peer app



## wanted specs



### efficient protocol

binary protocol based on flatbuffers

flatbuffers is a quasi-standard for efficient binary protocols

flatbuffers is a new version of protobuf (protocol-buffers)

text protocols are slow and verbose

bad examples

- JSON: nostr, ...
- XML: xmpp, ...



### efficient implementation

fuck javascript

fuck java

seriously...
people who still believe that javascript and java are a good idea
should be kicked out from any serious discussion

bad examples

- https://github.com/Bombe/Sone - written in java
- https://github.com/nostr-protocol - based on JSON to make javascript happy



### transparent moderation

aka: transparent censorship

aka: censorship without meta-censorship

lets be honest:
there are no "neutral platforms",
because only dead people are "neutral",
and all life has bias.

there are only publishers,
and every publisher has his bias (or his jurisdiction),
so every publisher wants to moderate content

one problem with the current situation of moderation is
that the current moderation is not transparent:
content is removed and leaves no trace,
aka "censorship" and "meta-censorship" (censoring the process of censorship)

to get "transparent moderation"
publisher must have the freedom to remove contents
but they must leave a trace (the metadata of the contents)
so the censored content can be found on a different publisher
who has decided "this content is legal in my domain"

publishers can decide to block all content by default, and only publish the metadata.
in this stage, the content is "unreviewed and blocked".
when the publisher has reviewed the content,
he can either publish the content as "reviewed and accepted",
or explicitly mark the content as "reviewed and blocked",
or leave the content as "unreviewed and blocked"

the metadata has no human-readable information,
so it is always safe to publish the metadata.
usually, this is a sha256-checksum and a signature of that checksum,
like in the nostr protocol.
the metadata also should have a pointer to the previous event,
so everyone can see the full [chain of events](#chain-of-events)

the censored content looks like a [censor bar](https://en.wikipedia.org/wiki/Censor_bars) in a censored paper document,
so that at least you can see that there was some content, but it was removed

see also [redaction](https://en.wikipedia.org/wiki/Redaction)

<blockquote>

Redaction or sanitization is the process of
removing sensitive information from a document
so that it may be distributed to a broader audience.

It is intended to allow the selective disclosure of information.

Typically, the result is a document that is suitable for publication
or for dissemination to others rather than the intended audience of the original document.

When the intent is secrecy protection, such as in dealing with classified information,
redaction attempts to reduce the document's classification level, possibly yielding an unclassified document.

When the intent is privacy protection, it is often called data anonymization.

</blockquote>

bad examples? virtually every app fails here.
either the moderation is too aggressive (censorship),
or the moderation is too permissive (no separation between metadata and content)

https://www.cato.org/briefing-paper/shining-light-censorship-how-transparency-can-curtail-government-social-media

</blockquote>

As Ray Bradbury observed, "There is more than one way to burn a book,"
and recent experience demonstrates that the same is true of government censorship.

When most people think about government censorship,
they imagine the firemen in Fahrenheit 451 burning books
or the Great Firewall in China blocking websites.

But government censorship, at least in the United States,
increasingly occurs in a more subtle fashion:
government officials informally pressuring or encouraging private actors,
such as social media companies, to suppress the speech of, or deny services to,
individuals with disfavored views—in other words, censorship by proxy.
This practice has also been colloquially referred to as "jawboning."

...

In matters of national security, law enforcement, and beyond,
government officials regularly make statements
that encourage private actors to suppress information,
and not all of this is objectionable.

Consider, for example, an FBI agent who requests that a newspaper
delay publishing certain details about an ongoing criminal investigation
because doing so could undermine attempts to capture the suspect.

...

There is an easier and more effective way to address censorship by proxy: transparency.

Federal officials should be required to publicly report attempts
to suppress Americans' exercise of speech and associational rights.

Censorship by proxy, as practiced today,
depends on secrecy and practical obscurity to evade public and legal accountability.

Forcing attempted censorship out of the shadows stands to deter
the worst abuses and ensure that officials who aren't deterred can be held to account.

</blockquote>



### offline first

do not rely on the internet

this should also work over ad-hoc decentral networks

- LAN
- WLAN
- bluetooth
- NFC
- QR codes
- printing and scanning of paper documents

similar to

- berty
- briar
- ssb
- retroshare



### nomadic identities

this is required to give power to users

if some publisher censors my content or deletes my account
then i am in full control of my data
and simply can go to a different publisher
and re-publish (re-upload) my content there

similar to

- ssb
- retroshare



### chain of events

i want to make sure that i receive a full chain of events
from some peer through some server
and the server did not remove some events (censorship)

similar to

- git: chain of commits
- ssb: chain of events

this is missing in the nostr protocol

see also

- https://github.com/nostr-protocol/nostr/issues/102
- https://github.com/nostr-protocol/nostr/issues/148
- https://github.com/nostr-protocol/nips/issues/419

social p2p network based on flatbuffers binary protocol moderation federation "offline first" scuttlebutt berty



### compression

checksums and signatures should be stored in binary form,
not as hex strings, not as base64 strings

there should be ways to store text contents in a compressed form,
allowing different compression algorithms and compression levels

some content has better compression with bzip2,
some content has better compression with zstd,
...

the compression should not be limited to one compression algorithm,
and it should allow to add new compression algorithms in the future

see also

- https://github.com/phiresky/sqlite-zstd https://news.ycombinator.com/item?id=32303762 Reduce SQLite database size by up to 80% with transparent compression



## see also

- https://en.wikipedia.org/wiki/Comparison_of_software_and_protocols_for_distributed_social_networking
- git-bug https://github.com/MichaelMure/git-bug/blob/master/doc/model.md
- fossil https://fossil-scm.org/home/doc/trunk/www/fossil-v-git.wiki
- radicle - not really "decentral", centralized by its bootstrap nodes
- bittorrent
  - gittorrent (old, broken) https://github.com/cjb/GitTorrent
  - zeronet https://github.com/HelloZeroNet/ZeroNet
- retroshare 
  - https://github.com/RetroShare/RetroShare
  - https://www.linux-magazine.com/Online/Features/RetroShare
- https://ssd.eff.org/ Surveillance Self-Defense. Tips, Tools and How-tos for Safer Online Communications
