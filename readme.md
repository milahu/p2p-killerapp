# p2p killerapp

my search for the perfect peer to peer app



## wanted specs



### efficient protocol

binary protocol based on flatbuffers

flatbuffers is a quasi-standard for efficient binary protocols

flatbuffers is a new version of protobuf (protocol-buffers)

text protocols are slow and verbose

the protocol should be machine-readable first, and human-readable second

the "canonical" form of the data should be optimized for high speed and small size.
this form is used for storage and transfer of data

from the machine-readable format, users can always generate human-readable formats, aka "disassembly".
but this case is rare, because most people dont need to "read the source"

bad examples

- JSON: nostr, ...
- XML: xmpp, ...

see also

- https://github.com/nostr-protocol/nips/pull/512 - a binary protocol for nostr
  - https://github.com/renostr/nrps/blob/master/nrp-1.md
- https://github.com/nostr-protocol/nips/pull/515 - a stupid workaround to make JSON faster



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



#### censortrace

> content is removed and leaves no trace

we need a way to detect censorship.

for example, i have the suspicion that most of my sent emails are censored,
so they are never delivered to the recipients, but i cannot prove it.

the emails just seem to disappear without a trace,
i get zero replies from recipients,
and i get no error message like

> Undelivered Mail Returned to Sender.
> error: rejected by spam filter

i assume the main problem here is gmail (google mail)

but i also assume that **all clearnet email providers**
are controlled by some secret service (CIA, MI6, Mossad, BND, FSB, MSS, ...)
who is actively manipulating message delivery
(active measures,
[controlling of others’ relationships](https://de.wikipedia.org/wiki/Bindungstoleranz),
control over mate choice,
no [freedom of association](https://en.wikipedia.org/wiki/Freedom_of_association),
gatekeeping of friendships,
control freaks,
...)

https://www.reddit.com/r/GMail/comments/1ba6026/emails_not_sending_no_bounce_message/

https://www.mailpool.ai/blog/the-phantom-bounce-why-your-emails-disappear-without-a-trace-and-how-to-fix-it

https://powerusers.codidact.com/posts/293711

https://www.reddit.com/r/GMail/comments/2892dr/is_gmail_silently_deleting_emails/

https://ntkp.substack.com/p/google-chrome-and-gmail-the-silent-c75

> Emails Selectively Blocked: Messages containing sensitive content, such as politically controversial information or whistleblower reports, are often blocked before reaching the intended recipient.

> Emails Silently Deleted: Certain emails just disappear from inboxes without warning, particularly those involving sensitive discussions.

> Shadowbanning & Isolation: Some individuals effectively find themselves cut off from communication as their messages are silently routed to spam folders across multiple platforms, reducing their visibility and engagement.

> Several whistleblowers, including former Google employees, have provided evidence that Gmail actively filters emails based on content-sensitive AI algorithms. Leaked internal documents have shown that emails containing political keywords or links to investigative journalism are flagged, downranked, or isolated.

> Google has invested heavily in AI-driven content control mechanisms that use machine learning to categorize, suppress, and modify information before it can spread. Some key elements include:
>
> Jigsaw Program: Initially developed to combat extremism, Jigsaw is now repurposed to filter political dissent and label certain narratives as “dangerous misinformation.”

> Targeted Individual Censorship: If a person is flagged as a “disruptive influence”—such as an independent journalist, human rights activist, or researcher—they may be shadow-banned across multiple Google services, including Gmail, Chrome, and YouTube.

> Google’s algorithmic filtering limits access to groundbreaking scientific research, alternative energy solutions, and medical breakthroughs. Researchers working on controversial or disruptive technologies often find their work suppressed or erased entirely.

> corporate interests

> Researchers who oppose the status quo or threaten the power structures of large corporations are often targeted by Google’s censorship infrastructure.

https://www.youtube.com/watch?v=FvmGIFShz9k

> Israel’s Final Solution For The Goyim
>
> NXR Studios
>
> 06.02.2026
>
> Israel's information warfare



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



### voting, tagging, trust

TODO

see also [doc/2025-09-04.generic-tagging-and-voting-system.md](doc/2025-09-04.generic-tagging-and-voting-system.md)



### p2p internet archive

keywords:

- decentralizing the internet archive
- decentralizing web.archive.org
- decentralizing archive.today

problem: archive.org is too centralized, archive.today is too centralized, ...

these services will not live forever,
especially now as the global trend towards more censorship
is getting more aggressive every day

so we need some kind of peer-to-peer internet archive

one challenge here is the problem of trust and voting:
why should i trust other peers to not modify the archived data?
how can i give feedback on the archived data hosted by other peers?
(feedback as in: upvotes, downvotes, comments, tags)

another challenge is the hosting incentive:
why should other peers host content that i value?
do i pay other peers for their hosting service?

another challenge is the discoverability of content:
assuming i have the original url of some content,
how do i find other peers who are hosting snapshots of this content?

see also [doc/2025-09-04.generic-tagging-and-voting-system.md](doc/2025-09-04.generic-tagging-and-voting-system.md)



### aggregation of multiple sources

every peer can upload its content to multiple publishers

globally, there are many many publishers,
and i want to subscribe to the news feeds of many peers

but i dont want to use some fancy webinterface for every publisher,
like protonmail.com, which offers no IMAP server for free accounts.

instead, i want a "news aggregator" (RSS reader, newsreader) to aggregate content
from many peers over many publishers

this should be more efficient than RSS,
more similar to git, where only missing data is transferred from server to client
= incremental updates



### personality types

users can rate themselves and others in terms of personality types

personality type questionnaires can be imported into the system,
so all users can publish their answers.
every question can be answered with an integer
between +100 ("yes") and -100 ("no")

related:
https://www.personality-database.com/



#### interpersonal compatibility

there are 2 reasons to like or hate people:
personal reasons and objective reasons.

there are 2 personal reasons to like people:
you follow them or they follow you.
(follow = trust = student)
(lead = influence = teacher)

there are infinite objective reasons,
which are encoded as tags ("hashtags")
which users can assign to others
with an integer weight
between +100 ("yes") and -100 ("no")

users can rate others based on these reasons.

ideally, at some point,
there should appear a pattern of human relations,
based on personality type and gender (male or female).
a possible solution for such a pattern of human relations
is the
[pallas pattern of human relations](https://github.com/milahu/alchi)



## possible project names

- tribesnet
  - stable tribes are the basis for this network
  - its not a "federation of tribes",
    because "federation" reminds of over-centralization
    (conspiracy, pacifism, fascism)
- mirrornet
  - every peer can mirror contents from other peers
- archivenet
  - every peer can archive contents from other peers
- relaynet
  - every peer can relay contents from other peers
- cachenet
  - every peer can cache contents from other peers
- uncensorednet
  - uncensored source of information
  - censorship-resistant hosting of all contents (yes also illegal contents)



## see also

- https://en.wikipedia.org/wiki/Comparison_of_software_and_protocols_for_distributed_social_networking
- git-bug https://github.com/MichaelMure/git-bug/blob/master/doc/model.md
- fossil https://fossil-scm.org/home/doc/trunk/www/fossil-v-git.wiki
- radicle - not really "decentral", centralized by its bootstrap nodes
- ssb https://github.com/ssbc
  - git-ssb https://git.scuttlebot.io/%25n92DiQh7ietE%2BR%2BX%2FI403LQoyf2DtR3WQfCkDKlheQU%3D.sha256
  - https://en.wikipedia.org/wiki/Secure_Scuttlebutt
- bittorrent
  - gittorrent (old, broken) https://github.com/cjb/GitTorrent
  - zeronet https://github.com/HelloZeroNet/ZeroNet
    - https://github.com/ZeroNetX/ZeroNet
- retroshare 
  - https://github.com/RetroShare/RetroShare
  - https://www.linux-magazine.com/Online/Features/RetroShare
- berty https://github.com/berty/berty - offline first, bluetooth, wifi
- jami https://git.jami.net/savoirfairelinux/jami-client-qt - alternative to Telegram
  - https://docs.jami.net/en_US/user/introduction.html#how-does-jami-work - Jami uses a distributed hash table (DHT) to connect peers. Jami accounts are asymmetric X.509 certificates generated by the GnuTLS library. Calls are made over the Session Initiation Protocol (SIP) after negotiating a TLS-encrypted secure connection, performing Secure Real-time Transport Protocol (SRTP) communication which carries the media streams.
  - https://docs.jami.net/en_US/user/jami-distributed-network.html - "too distributed"?
  - https://docs.jami.net/en_US/user/lan-only.html
  - https://docs.jami.net/en_US/developer/protocol.html
  - https://docs.jami.net/en_US/developer/technical-overview.html
- https://en.wikipedia.org/wiki/Minds_(social_network)
  - Writers in The New York Times, Engadget, and Vice have noted the volume of far-right users and content on the platform, following a trend across social media.
    Minds describes itself as focused on free speech, and minimally moderates the content on its platform.
  - Vice criticized Minds in 2019 as a "haven" for neo-Nazis and far-right groups and individuals.
    In response to the 2019 allegations, the site banned several neo-Nazis and people belonging to other hate groups.
    Nathaniel Popper wrote for The New York Times in 2021 that
    Minds "became an online home to some of the right-wing personalities and neo-Nazis
    who were booted from mainstream social networks, along with fringe groups, in other countries,
    that have been targeted by their governments".
  - Ottman has said that he opposes removing hate speech and other objectionable content from Minds
    because he believes it can draw more attention to it,
    and that he opposes deplatforming extremists
    because he believes it only serves to push people
    towards more "other darker corners of the internet".
    In a 2019 statement to Vice,
    Minds executives expressed their belief that
    "free expression and transparency as the antidote
    to radicalization, violence, and extremism".
- https://en.wikipedia.org/wiki/Gab_(social_network)
  - https://news.gab.com/2023/08/gab-emerges-as-the-true-speech-platform-contrasting-the-adls-strategy-for-x-twitter/
- mixnets: mixmaster and mixminion  - high-latency onion routing gives better anonymity than low-latency onion routing (Tor, I2P)
  - https://www.csoonline.com/article/566269/are-mixnets-the-answer-to-anonymous-communications.html
  - https://security.stackexchange.com/questions/150232/logging-attack-tor-vs-mixnets
- i2p
  - https://geti2p.net/en/comparison/other-networks
- disaster.radio https://disaster.radio/ - When the critical infrastructure that so many of us take for granted goes away, how do we organize ourselves and our communities to respond?
  If recent ecological disasters have demonstrated anything, it is the inadequacy of existing models and tools to provide efficient allocation of resources, access to emergency communications, and effective coordination of human effort. Few if any solutions exist that are off-grid, affordable, reliable, easily deployed, and openly standardized.
  disaster.radio addresses this problem.
- radicle
  - https://groups.google.com/a/monadic.xyz/g/radicle/c/ctR0tgua7Wo - Radicle, but using SSB instead of IPFS?
  - https://github.com/radicle-dev/radicle-alpha/issues/689 - We will be moving away from IPFS, and most likely also from the client-server architecture
    - IPFS, Dat, SSB all have immutable append-only hash-based approaches, but git already does this better than most of them.
      But this approach isn't the best for managing state.
      State needs to be mutable, and fast.
      Can I ask why you never considered [GUN](https://github.com/amark/gun)? We're faster than many centralized databases, yet completely P2P/decentralized and trustless (cryptographically secure).
- NNTP: Network News Transfer Protocol
  - aka "usenet"
  - https://en.wikipedia.org/wiki/Network_News_Transfer_Protocol
  - https://github.com/mrusme/superhighway84 - USENET-inspired, uncensorable, decentralized internet discussion system running on IPFS & OrbitDB
- https://ssd.eff.org/ Surveillance Self-Defense. Tips, Tools and How-tos for Safer Online Communications
- https://github.com/2gatherproject/decentralized-social-apps-guide#githubgitlab-alternatives
- https://github.com/gdamdam/awesome-decentralized-web#collaboration
- https://github.com/markqvist/Reticulum - The cryptography-based networking stack for building unstoppable networks with LoRa, Packet Radio, WiFi and everything in between.
  - https://reticulum.network/
  - https://github.com/BeechatNetworkSystemsLtd/Reticulum-rs
  - https://github.com/BeechatNetworkSystemsLtd/rns-vpn-rs
    - https://www.reddit.com/r/selfhosted/comments/1nqyr8h/we_built_a_p2p_vpn_that_runs_over_a_reticulum/
  - https://github.com/markqvist/lxmf
  - https://github.com/markqvist/sideband
  - https://unsigned.io/website/hardware/RNode.html
    - While speeds are lower than WiFi, typical communication ranges are many times higher. Several kilometers can be acheived with usable bitrates, even in urban areas, and over 100 kilometers can be achieved in line-of-sight conditions.
- https://github.com/Tribler/tribler
  - https://www.tribler.org/anonymity.html
  - https://github.com/Tribler/tribler/wiki/Hidden-Services-Specifications-for-anonymous-seeding
  - https://github.com/Tribler/tribler/wiki/Anonymous-Downloading-and-Streaming-specifications
- gitgeist
  - [gitgeist: a git-based social network proof of concept](http://web.archive.org/web/20250914132649/https://www.karimyaghmour.com/blog/2019/02/gitgeist-a-git-based-social-network-proof-of-concept.html)
    - "Looks like reinventing www.fossil-scm.org"
    - "good luck with scaling and hosting" https://github.com/CocoaPods/CocoaPods/issues/4989#issuecomment-193772935
  - [gitgeist: a git-based social network proof of concept @ lwn.net](https://lwn.net/Articles/780365/)
  - https://github.com/opersys/gitgeist-poc
