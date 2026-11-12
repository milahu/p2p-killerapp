# Semantic Web Software Projects

**User:** Anonymous  
**Created:** 2026/11/12 17:01:25  
**Updated:** 2026/11/12 17:16:41  
**Exported:** 2026/11/12 17:18:27  
**Link:** [<https://chatgpt.com/c/6af5e2d5-0d0c-83eb-96d5-1e21cb24663c>](https://chatgpt.com/c/6af5e2d5-0d0c-83eb-96d5-1e21cb24663c)

## Prompt:

11/12/2026, 5:01:59 PM

do you know some software solutions for a "generic semantic web of everything"?  
for example, one small aspect of that "everything" could be the challenge to merge/align/match multiple media catalogs, for example matching the movie catalog from IMBD (using some public dump of their database) with a bittorrent catalog from a DHT dump (using only the torrent names as data source). the challenge is that this is a huge piece of work (manually checking and fixing the alignments suggested by an automatic alignment algorithm, and also improving the automatic alignment algorithm so it makes less errors in the future), so this requires many people working on this project, which directly leads to the biggest challenge of all: social problems, mainly the problem of trust, because as soon as i delegate some piece of work to somebody else then i trust that someone to produce correct results, but this trust can be exploited to produce garbage data ("index poisoning")... so inevitably, humans will also have to be tracked as "objects" in this "generic semantic web of everything", because "humans are just objects", with different types of relations (graph edges) to each other (somewhere between "trust" and "distrust"). this "generic semantic web of everything" should work for any type of object, for example also as a generic tagging and voting system, where users can assign their tags and votes on objects, and other users can use these tags and votes to derive recommendations for their own "feed". so i guess i am also looking for some kind of open-source "social network", where all the "algorithms" (recommendation algorithms, suggestion algorithms) are open-source, and all users have the freedom to write their own algorithms to consume all the raw data in the way they want... so, do you know some software projects with this "megalomanic" scope? a slogan of such a project could be "connect all the dots!" or "connect all the things!"

## Response:

11/12/2026, 5:02:07 PM

> **Searched 14 websites**
>
> Worked for 20s

Yes. And I think what you're describing is considerably more interesting than just a "semantic web" or a "knowledge graph."

You're essentially describing a **decentralized, collaborative, trust-aware knowledge graph of arbitrary entities**, where:

- **Everything is an entity:** Movies, torrents, people, organizations, websites, concepts, tags, assertions, algorithms, even other relationships.
- **Everything can be connected:** Through typed relationships, including fuzzy, uncertain, contradictory, or subjective ones.
- **Anybody can contribute:** By creating entities, proposing relationships, correcting mistakes, assigning tags, or voting.
- **Nobody has to trust everybody:** Contributions have provenance, and trust can be calculated individually rather than enforced by a central authority.
- **Algorithms are interchangeable:** Users can choose their own matching, ranking, filtering, reputation, and recommendation algorithms.
- **Disagreement is preserved:** Instead of enforcing a single global truth, the system can represent competing claims and let users decide whose claims to trust.
- **The entire system is extensible:** Not just the data schema, but also the algorithms used to interpret that data.

The particularly interesting part is that **trust itself becomes graph data**. A user's reputation isn't necessarily one globally agreed-upon number. It could depend on who is evaluating them, which domain they're working in, and what evidence exists.

For example, I might trust Alice's movie metadata corrections but distrust her political classifications. Bob might trust Alice on both. Neither of us should have to accept the other's trust model.

There are several open-source projects that approach this vision from different directions. Some have remarkably ambitious scopes.

## 1. The projects I'd investigate first

These are the strongest candidates, ranked by how closely they approach different aspects of your vision, rather than by popularity.

<box gap={3}>
  <row align=start gap={3}>
    <AsyncImage query="Wikidata Wikibase knowledge graph logo" aspectRatio="1:1" maxWidth="92px"/>
    <box flex="1" gap={1}>
      <row align=center wrap="wrap" gap={2}>
        **1. <Entity category="software" value="Wikibase"/> / <Entity category="organization" value="Wikidata"/>**
        <badge color="success">Closest knowledge model</badge>
      </row>
      <text color="secondary" size="xs">Collaborative knowledge graph · Entity IDs · Statements · References</text>
      Probably the closest existing implementation of the "everything is an object" part. Wikibase supports arbitrary entities, typed properties, qualifiers, references, and collaborative editing. Wikidata demonstrates the approach at enormous scale.

      **Missing:** Personalized trust, subjective voting, user-defined feeds, and decentralized authority are not native design priorities.

      <text size="sm"><Link url="https://www.wikibase.cloud/" title="Wikibase"/> · <Link url="https://www.wikidata.org/" title="Wikidata"/> <Cite ref="turn928390search15"/></text>
    </box>

  </row>
  <divider color="subtle"/>
  <row align=start gap={3}>
    <AsyncImage query="AT Protocol Bluesky logo butterfly" aspectRatio="1:1" maxWidth="92px"/>
    <box flex="1" gap={1}>
      **2. <Entity category="software" value="AT Protocol"/> (Bluesky ecosystem)**

      <text color="secondary" size="xs">Decentralized social data · Custom algorithms · Public event stream</text>
      This is exceptionally relevant to your requirement that users can build their own recommendation algorithms. The protocol supports extensible record types, public data streams, and independent feed generators.

      **Missing:** It isn't inherently a semantic knowledge graph, and trust-aware entity reconciliation would need to be built on top.

      <text size="sm"><Link url="https://atproto.com/" title="AT Protocol"/> · <Link url="https://atproto.com/guides/feeds" title="Custom feed documentation"/> <Cite refs={["turn928390search7","turn928390search3"]}/></text>
    </box>

  </row>
  <divider color="subtle"/>
  <row align=start gap={3}>
    <AsyncImage query="Solid Project decentralized web logo" aspectRatio="1:1" maxWidth="92px"/>
    <box flex="1" gap={1}>
      **3. <Entity category="software" value="Solid Project"/>**

      <text color="secondary" size="xs">Linked Data · Personal data ownership · Decentralization</text>
      Tim Berners-Lee's broader effort to separate applications from data ownership. Solid Pods store interoperable data, including linked data, with user-controlled access.

      **Missing:** No built-in global reconciliation community, reputation engine, or universal recommendation system.

      <text size="sm"><Link url="https://solidproject.org/" title="Solid Project"/> <Cite ref="turn928390search12"/></text>
    </box>

  </row>
  <divider color="subtle"/>
  <row align=start gap={3}>
    <AsyncImage query="OpenRefine software logo" aspectRatio="1:1" maxWidth="92px"/>
    <box flex="1" gap={1}>
      **4. <Entity category="software" value="OpenRefine"/>**

      <text color="secondary" size="xs">Entity reconciliation · Human verification · Data cleaning</text>
      Directly relevant to the IMDb/torrent example. It provides a reconciliation workflow for matching external records, reviewing candidates, and correcting mismatches.

      **Missing:** It's primarily a data-cleaning tool, not a massively collaborative, decentralized social knowledge platform.

      <text size="sm"><Link url="https://openrefine.org/" title="OpenRefine"/> <Cite ref="turn928390search11"/></text>
    </box>

  </row>
</box>

These four are complementary rather than competing solutions. In fact, combining their architectural ideas might get surprisingly close to what you want.

## 2. More ambitious and unusual projects

These are worth investigating because they address the social, philosophical, or architectural problems that traditional knowledge graphs tend to ignore.

| Project | Interesting feature | Main limitation |
|----|----|----|
| <Link url="https://github.com/Trustroots/ask" title="Trustroots"/> | Social trust and community relationships | Not a generic semantic graph |
| <Link url="https://github.com/ssbc" title="Secure Scuttlebutt (SSB)"/> | Signed social messages, peer-to-peer replication, subjective social graphs | Smaller ecosystem, limited semantic structure |
| <Link url="https://nostr.com/" title="Nostr"/> | Signed, extensible events; independent relays and clients | Entity schemas and reputation conventions are fragmented |
| <Link url="https://www.metacurrency.org/" title="Holochain"/> | Agent-centric distributed applications, validation rules, local perspectives | Framework rather than ready-made universal knowledge network |
| <Link url="https://www.metacurrency.org/" title="Ceptr / MetaCurrency"/> | Very ambitious composable semantic computing ideas | Experimental and not a turnkey platform |
| <Link url="https://github.com/ActivityWatch/activitywatch" title="ActivityWatch"/> | Open-source event capture for personal activity data | Primarily personal activity tracking |
| <Link url="https://github.com/hypothesis" title="Hypothesis"/> | Collaborative annotations attached to arbitrary web resources | Annotation-centered rather than a universal graph |
| <Link url="https://www.openstreetmap.org/" title="OpenStreetMap"/> | Large-scale collaborative object editing, tags, history, anti-vandalism practices | Geographically focused |
| <Link url="https://www.metabrainz.org/" title="MetaBrainz / MusicBrainz"/> | Community-curated identity resolution, edits, voting, persistent identifiers | Primarily media metadata |

I'd particularly emphasize **Secure Scuttlebutt, Nostr, Holochain, and MusicBrainz**.

MusicBrainz is interesting because it has years of practical experience with the exact human problem you're describing: contributors disagreeing about whether two records refer to the same real-world entity, with mechanisms for proposing and reviewing edits.

Secure Scuttlebutt is interesting for almost the opposite reason: it approaches the network from the perspective of individual participants and their social relationships, rather than assuming a single authoritative database.

One caution: several of the more experimental projects have changed substantially over time. I'd assess repository activity, maintained implementations, and community health before adopting them.

## 3. The missing piece: subjective trust and reputation

This is where your vision differs fundamentally from Wikidata and most existing knowledge graphs.

Consider a simple example:

<box border radius="xl" padding={3} gap={2}>
  <text weight="medium" size="sm">Example: a disputed movie catalog match</text>
  <svg viewBox="0 0 340 224" width="100%" xmlns="http://www.w3.org/2000/svg">
    <rect x="8" y="12" width="138" height="45" rx="9" fill="#64748b" fillOpacity=".12" stroke="#94a3b8"/>
    <text x="77" y="30" fontSize="11" textAnchor="middle" fill="currentColor" fontWeight="600">IMDb entity</text>
    <text x="77" y="45" fontSize="10" textAnchor="middle" fill="currentColor">tt0133093</text>
    <rect x="194" y="12" width="138" height="45" rx="9" fill="#64748b" fillOpacity=".12" stroke="#94a3b8"/>
    <text x="263" y="30" fontSize="11" textAnchor="middle" fill="currentColor" fontWeight="600">Torrent entity</text>
    <text x="263" y="45" fontSize="10" textAnchor="middle" fill="currentColor">The.Matrix.1999...</text>
    <path d="M146 34 H194" stroke="#0D9488" strokeWidth="2" strokeDasharray="5 3"/>
    <rect x="122" y="67" width="96" height="23" rx="11" fill="#0D9488" fillOpacity=".15"/>
    <text x="170" y="82" fontSize="10" textAnchor="middle" fill="#0D9488">match claim</text>
    <path d="M170 57 V67 M170 90 V113" stroke="#94a3b8" strokeWidth="1.5"/>
    <rect x="110" y="113" width="120" height="32" rx="8" fill="#64748b" fillOpacity=".12" stroke="#94a3b8"/>
    <text x="170" y="133" fontSize="11" textAnchor="middle" fill="currentColor">Assertion #782</text>
    {#each [{x:9,t:"Alice",s:"supports",c:"#0D9488"},{x:119,t:"Bob",s:"disputes",c:"#DC6B47"},{x:229,t:"Matcher v3",s:"proposes",c:"#64748b"}] as n}
      <path d={`M170 145 L${n.x+51} 170`} stroke={n.c} strokeWidth="1.5"/>
      <rect x={n.x} y="170" width="102" height="41" rx="8" fill={n.c} fillOpacity=".12" stroke={n.c}/>
      <text x={n.x+51} y="186" fontSize="11" textAnchor="middle" fill="currentColor" fontWeight="600">{n.t}</text>
      <text x={n.x+51} y="200" fontSize="10" textAnchor="middle" fill={n.c}>{n.s}</text>
    {/each}
  </svg>
  <caption>Illustrative graph: the match is an assertion with its own identity, provenance, and competing evaluations.</caption>
</box>

The crucial design decision is that the relationship *itself* is an entity.

Instead of storing:

`Torrent X → matches → IMDb Y`

you store an assertion with an identity, author, evidence, algorithm version, timestamp, and evaluations from other users.

That lets you answer questions like:

- Which assertions were produced by an algorithm that later turned out to be unreliable?
- Which reviewers consistently catch its mistakes?
- Which reviewers agree with people I trust?
- Which assertions should be reconsidered after new evidence appears?
- Which users have suspiciously correlated voting patterns?

This leads to a particularly powerful principle:

**Don't store one universally accepted graph. Store an open graph of claims, and let each participant derive their own trusted view of it.**

The raw data can be shared, while the interpretation remains personal.

### Existing research worth exploring

Several established ideas address parts of this:

- **<Entity category="scientific_concept" value="Web of Trust"/> / EigenTrust:** Computing trust through relationships and historical behavior.
- **<Entity category="scientific_concept" value="Subjective logic"/>:** Representing belief, disbelief, and uncertainty, rather than reducing everything to a single score.
- **<Entity category="scientific_concept" value="Sybil attack"/> resistance:** Preventing one attacker from manufacturing thousands of apparently independent contributors.
- **<Entity category="scientific_concept" value="Truth discovery"/>:** Estimating claim reliability when sources disagree and their reliability is itself unknown.
- **W3C PROV-O:** Standardized provenance for tracing how information was produced.
- **<Link url="https://www.w3.org/TR/rdf12-concepts/" title="RDF 1.2"/> and named graphs:** Foundations for expressing linked statements and their context.

One subtle point: a cryptographic signature establishes who controlled a signing key, not whether the signed claim is true. And agreement between 100 accounts isn't strong evidence if all 100 are controlled by one adversary.

## 4. What I would build from existing components

I wouldn't begin by inventing an entirely new graph database or decentralized protocol.

I'd build a prototype around four layers.

<box border radius="xl" padding={3} gap={2}>
  <box background="surface-secondary" radius="lg" padding={3} align=center gap={1}>
    **Applications and personalized feeds**
    <text color="secondary" size="xs" textAlign="center">Custom recommendation engines · Search · Tags · Voting · Exploration</text>
  </box>
  <row justify="center"><icon name="arrow-up-down" color="tertiary"/></row>
  <box background="surface-secondary" radius="lg" padding={3} align=center gap={1}>
    **Trust and interpretation**
    <text color="secondary" size="xs" textAlign="center">Personal trust policies · Reputation · Claim filtering · Conflict resolution</text>
  </box>
  <row justify="center"><icon name="arrow-up-down" color="tertiary"/></row>
  <box background="surface-secondary" radius="lg" padding={3} align=center gap={1}>
    **Shared assertions and provenance**
    <text color="secondary" size="xs" textAlign="center">Entities · Relationships · Signed claims · Evidence · Review history</text>
  </box>
  <row justify="center"><icon name="arrow-up-down" color="tertiary"/></row>
  <box background="surface-secondary" radius="lg" padding={3} align=center gap={1}>
    **Open storage and synchronization**
    <text color="secondary" size="xs" textAlign="center">Wikibase/RDF · PostgreSQL · AT Protocol or event replication</text>
  </box>
</box>

For a first working system, I'd use:

| Component                | Candidate                                        |
|--------------------------|--------------------------------------------------|
| Knowledge model          | Wikibase-style entities and statements           |
| Storage                  | PostgreSQL initially, optionally RDF             |
| Catalog matching         | OpenRefine, RapidFuzz, Splink                    |
| Collaborative review     | MusicBrainz-inspired edit proposals and voting   |
| Provenance               | W3C PROV-O, signed append-only events            |
| Social data distribution | AT Protocol or Nostr                             |
| User algorithms          | Independent feed/indexing services               |
| Trust                    | Pluggable, domain-specific reputation algorithms |

For the movie example, I'd also distinguish *movie*, *edition*, *release*, *file*, and *torrent* as different entities. A torrent filename might be ambiguous, misleading, or refer to a collection rather than a single film. Collapsing those entities prematurely would create errors that no trust algorithm could reliably repair.

And I would keep the matching algorithm's confidence separate from the community's confidence in the resulting assertion.

## 5. A particularly promising philosophy: make disagreement a first-class feature

Most collaborative databases assume the ultimate goal is to arrive at a single correct answer.

But your system could work differently.

Suppose Alice thinks a movie is science fiction, Bob thinks it's fantasy, and Charlie thinks it belongs to both genres.

All three assessments can coexist.

A recommendation algorithm might use Alice's classification, another might use Charlie's, and a third might infer genre probabilities from the entire network.

For factual catalog matching, evidence and verification would carry more weight. For subjective tagging, personal preference and social similarity would matter more.

In other words, **the graph doesn't need to decide what's true, relevant, or interesting. It needs to preserve enough information for different algorithms to make those decisions.**

This also suggests that algorithms should themselves be entities in the graph: versioned, attributed, evaluated, and linked to the assertions they produce.

There are important privacy boundaries, though. Publicly recording identifiable people's trust relationships, negative assessments, or inferred traits can create serious privacy and abuse risks. Pseudonymous identities, selective disclosure, and private trust calculations would be important design choices.

## 6. My shortlist

If I were investigating this seriously, I'd prioritize these five:

1.  **Wikibase** - for the universal entity and assertion model.
2.  **AT Protocol** - for an extensible social data network with user-selectable algorithms.
3.  **Secure Scuttlebutt** - for its peer-centric approach to identity, replication, and trust.
4.  **MusicBrainz** - for real-world experience with collaborative entity reconciliation and human review. Its edit voting and editor privilege system are especially relevant. \<Cite refs={\["turn239203search0","turn239203search1"\]}/\>
5.  **Holochain** - for exploring an agent-centric alternative to globally authoritative state.

None of these is the complete "semantic web of everything" you described. But they provide useful foundations without having to start from zero.

------------------------------------------------------------------------

## One question that fundamentally changes the architecture

There are two rather different interpretations of your vision, and I'm curious which one is closer to yours.

{@body const \[choice,setChoice\] = DIL.useState("decentralized")}  
<box gap={3}>  
<radio-group direction="col" value={choice} onChange={setChoice}>  
<radio value="centralized">  
**A. One global graph, with personalized views**

      Everybody contributes to a common database. Trust algorithms determine which parts each user sees or believes. Think "Wikidata + Reddit + personalized trust."
    </radio>
    <radio value="decentralized">
      **B. A decentralized graph of independently published assertions**

      Everybody can publish their own claims and maintain their own graph. Nodes synchronize information selectively, and there is no globally authoritative version of reality. Think "Semantic Web + Secure Scuttlebutt + AT Protocol."
    </radio>
    <radio value="hybrid">
      **C. A hybrid**

      Shared public infrastructure and indexes for efficiency, but independent ownership of assertions, portable identities, and freedom to build competing interpretations.
    </radio>

  </radio-group>
  <button block onClick={()=>GenUI.issueNewTurn(({centralized:"I'm leaning toward one global graph with personalized trust views.",decentralized:"I'm leaning toward a decentralized graph of independently published assertions.",hybrid:"I'm leaning toward a hybrid architecture with shared indexes but independent assertions and trust."})[choice]+" Please go deeper into existing open-source projects and architectural tradeoffs for that approach.")}>Explore this architecture <icon name="arrow-right" inline/></button>
</box>

My own architectural preference would be **C**, because globally discoverable entities and large-scale matching benefit enormously from shared indexes, while decentralized assertions and subjective trust protect against a single authority controlling what counts as truth.

But I'd be interested in your preference, especially whether decentralization is a fundamental requirement or whether **algorithmic freedom and resistance to index poisoning** matter more to you than decentralization itself.

## Prompt:

11/12/2026, 5:10:11 PM

# Selected text:

## Selection 1

Shared public infrastructure and indexes for efficiency, but independent ownership of assertions, portable identities, and freedom to build competing interpretations.

Explore this architecture

## My request:

yes, that sounds like a good hybrid solution.  
one giant database of everything would be a waste of disk space.  
each node should have the freedom to decide which part of the global network he is interested in, so he can download and participate in that part of the global network.  
similar to git repositories: nobody wants to download everything of github, that would be a terrible waste of diskspace.  
so this "partitioning" should be a first-class feature.  
but compared to git repos, users can build relations between objects from different "roots".  
another project that comes to my mind is NOSTR, but NOSTR is just a stupid "message exchange protocol" (transport layer), lacking all the higher semantic features i want... (plus, NOSTR is based on JSON messages, so its rather inefficient....)

## Response:

11/12/2026, 5:10:19 PM

> **Searched 7 websites**
>
> Worked for 8s

I think **partitioning is the key architectural requirement** that distinguishes your idea from most existing semantic-web projects.

What you're describing is not simply a distributed knowledge graph. It's something closer to:

**A federated, selectively replicated, trust-aware graph of independently published assertions, with globally addressable entities and cross-partition relationships.**

And your Git analogy is excellent, with one important extension:

> Git lets you clone a repository and reference objects by hash. Your system should let you subscribe to arbitrary subsets of a global graph, including relationships that cross repository boundaries, without requiring you to clone the repositories containing those relationships' endpoints.

That last requirement is where things become architecturally interesting.

## 1. Partitioning should not be the same as ownership

I would separate three concepts that many systems conflate.

| Concept | Meaning | Example |
|----|----|----|
| **Identity** | What object or assertion is being referenced? | IMDb title `tt0133093` |
| **Ownership / authority** | Who published or controls a particular assertion? | Alice signed a claim |
| **Storage / subscription** | Which nodes choose to retain that assertion? | Three movie-indexing nodes |

An entity doesn't need to reside in one canonical partition.

A movie can be referenced by a torrent-indexing community, a film-review community, and a subtitle-indexing community, without any of them needing to download all the others' data.

Likewise, a relationship should not automatically inherit the storage requirements of either endpoint.

Imagine:

- Partition A: movie metadata
- Partition B: torrent metadata
- Partition C: claims matching torrents to movies
- Partition D: reviews of those matching claims

A user interested only in catalog reconciliation could subscribe to C and a limited projection of A and B, rather than all four partitions.

That gives you **selective replication at the level of graph meaning**, not merely at the level of storage files.

## 2. The project I'd now put at the top of your reading list: Willow

<row align=start gap={3}>
  <AsyncImage query="Willow protocol peer to peer synchronization project logo" aspectRatio="1:1" maxWidth="104px"/>
  <box flex="1" gap={1}>
    **<Link url="https://willowprotocol.org/" title="Willow Protocol"/>**

    Willow is a particularly interesting match for your *partitioning-first* requirement. It is designed around structured data namespaces, selective synchronization, and efficient reconciliation between peers.

  </box>
</row>

Its synchronization design includes exchanging areas of interest and efficiently identifying which entries differ, rather than retransmitting everything. <Cite ref="turn847394search2"/>

That's much closer to the replication substrate you want than a traditional blockchain or a globally replicated event log.

But Willow isn't a semantic-web application. You would still need to define entities, assertions, cross-partition links, trust semantics, and graph queries.

I'd investigate whether its namespace and area model could provide the foundation for semantic subscriptions.

## 3. The most difficult problem: cross-partition discovery

Suppose your local node contains the IMDb entity for *The Matrix*.

Somewhere else, a user publishes a relationship between that movie and a torrent.

How would your node discover this new relationship?

This is fundamentally different from following an outgoing link.

<box border radius="xl" padding={3} gap={2}>
  <svg viewBox="0 0 340 190" width="100%">
    <rect x="8" y="12" width="140" height="57" rx="9" fill="#0D9488" fillOpacity=".12" stroke="#0D9488"/>
    <text x="78" y="31" textAnchor="middle" fontSize="11" fontWeight="600" fill="currentColor">Partition A</text>
    <text x="78" y="46" textAnchor="middle" fontSize="10" fill="currentColor">Movie entity</text>
    <text x="78" y="59" textAnchor="middle" fontSize="9" fill="currentColor">Stored locally</text>
    <rect x="192" y="12" width="140" height="57" rx="9" fill="#64748b" fillOpacity=".12" stroke="#94a3b8"/>
    <text x="262" y="31" textAnchor="middle" fontSize="11" fontWeight="600" fill="currentColor">Partition B</text>
    <text x="262" y="46" textAnchor="middle" fontSize="10" fill="currentColor">Torrent entity</text>
    <text x="262" y="59" textAnchor="middle" fontSize="9" fill="currentColor">Stored remotely</text>
    <rect x="90" y="111" width="160" height="45" rx="9" fill="#64748b" fillOpacity=".12" stroke="#94a3b8"/>
    <text x="170" y="129" textAnchor="middle" fontSize="11" fontWeight="600" fill="currentColor">Partition C</text>
    <text x="170" y="144" textAnchor="middle" fontSize="10" fill="currentColor">Match assertion</text>
    <path d="M78 69 L125 111 M262 69 L215 111" stroke="#64748b" strokeWidth="1.8" strokeDasharray="5 4"/>
    <text x="170" y="89" textAnchor="middle" fontSize="10" fill="#D97706">Who discovers this edge?</text>
    <path d="M170 156 V177" stroke="#94a3b8" strokeWidth="1.5"/>
    <text x="170" y="188" textAnchor="middle" fontSize="9" fill="currentColor">Independent publisher</text>
  </svg>
</box>

There are several possible solutions:

- **Distributed reverse indexes:** Peers advertise which assertions reference a given entity.
- **Topic-based subscriptions:** Nodes follow specific entity types, predicates, or namespaces.
- **Community-maintained indexes:** Specialized nodes index all movie-to-torrent assertions.
- **Gossip and discovery:** Peers exchange compact summaries of newly available assertions.
- **Search services:** Independent index providers expose query APIs without controlling the underlying assertions.

I'd combine these approaches rather than mandate one.

A critical distinction is that **an index is not an authority**. It is merely one provider's potentially incomplete view of the network.

A malicious index could omit assertions just as easily as it could inject garbage. Therefore, signed assertions protect integrity, but multiple independently operated indexes and verifiable synchronization are needed to address completeness and censorship.

There is also an unavoidable tradeoff: you cannot guarantee discovery of every globally published incoming edge while requiring no global index, no global broadcast, and no exhaustive search. The architecture must explicitly define which completeness guarantees it offers.

## 4. Semantic subscriptions instead of repositories

I think the ideal subscription model would eventually look something like this:

<box border radius="xl" padding={3} gap={3}>
  <text weight="medium">Illustrative node subscription</text>
  {@body const [domain,setDomain] = DIL.useState("movies")}
  {@body const [claims,setClaims] = DIL.useState(true)}
  {@body const [reviews,setReviews] = DIL.useState(true)}
  {@body const [remote,setRemote] = DIL.useState(false)}
  {@body const [trust,setTrust] = DIL.useState("trusted")}
  <box gap={1}>
    <label>Primary domain</label>
    <radio-group direction="col" value={domain} onChange={setDomain}>
      <radio value="movies">Movies and media releases</radio>
      <radio value="software">Software projects and dependencies</radio>
      <radio value="science">Scientific publications and citations</radio>
    </radio-group>
  </box>
  <divider color="subtle"/>
  <checkbox checked={claims} onChange={setClaims} lineThrough={false}>Replicate cross-partition matching assertions</checkbox>
  <checkbox checked={reviews} onChange={setReviews} lineThrough={false}>Replicate votes, corrections, and provenance</checkbox>
  <checkbox checked={remote} onChange={setRemote} lineThrough={false}>Replicate full remote endpoint objects</checkbox>
  <box gap={1}>
    <label>Replication trust policy</label>
    <radio-group direction="col" value={trust} onChange={setTrust}>
      <radio value="all">All discoverable assertions</radio>
      <radio value="trusted">Only selected communities and publishers</radio>
    </radio-group>
  </box>
  <box background="surface-secondary" radius="lg" padding={3} gap={2}>
    <text color="secondary" weight="medium" size="xs">Conceptual subscription policy</text>
    <text size="xs" preserveWhitespace>{`domain: ${domain}
include_cross_partition_claims: ${claims}
include_reviews_and_provenance: ${reviews}
fetch_remote_objects: ${remote}
publisher_policy: ${trust}`}</text>
    <button color="secondary" variant="outline" size="sm" block onClick={()=>GenUI.copy(`domain: ${domain}\ninclude_cross_partition_claims: ${claims}\ninclude_reviews_and_provenance: ${reviews}\nfetch_remote_objects: ${remote}\npublisher_policy: ${trust}`)}><icon name="copy" inline/> Copy policy</button>
  </box>
</box>

This is just a conceptual interface, not an existing protocol.

The interesting consequence is that partitions needn't be fixed by their original publisher. A subscriber could construct a *virtual partition* based on a graph query.

For example:

`All assertions about movies released between 1990 and 2000, plus all evaluations of those assertions by publishers in my trust network.`

Implementing arbitrary semantic queries over decentralized data is difficult, though. Efficient synchronization generally needs restricted, indexable subscription predicates. Fully arbitrary graph queries would require specialized indexes or remote query execution.

I would make that distinction explicit in the protocol.

## 5. About Nostr and JSON

I agree with your main criticism, with one qualification.

Nostr isn't *only* transport. NIP-01 already defines signed events, event identifiers, references, kinds, and filtered subscriptions. <Cite ref="turn847394search0"/>

But those mechanisms don't provide the rich semantic data model, ontology alignment, provenance-aware graph queries, or fine-grained replication semantics you're looking for.

And JSON is not necessarily the biggest performance problem.

A compact binary encoding such as CBOR or Protocol Buffers could reduce serialization overhead. However, for a large graph, the bigger costs may be:

- Indexing arbitrary relationships and reverse references.
- Synchronizing millions of small assertions.
- Repeated identifiers and cryptographic signatures.
- Maintaining materialized graph views.
- Discovering relevant data across partitions.

I'd avoid tying the conceptual graph model to JSON, RDF serialization, or any other wire representation.

For example, define a canonical abstract assertion format and support a compact binary encoding. That also allows interoperability adapters for RDF, Wikibase, Nostr, or other ecosystems.

One caveat: if assertion IDs are content hashes, canonicalization must be precisely specified. Two equivalent assertions encoded differently must not accidentally produce incompatible identities unless that distinction is intentional.

## 6. A few architectural principles I'd make non-negotiable

1.  **Global addressability without global storage.** Any entity or assertion can be referenced without being locally available.
2.  **Independent replication policies.** Every node decides what to store, index, forward, and discard.
3.  **Assertions are immutable and attributable.** Corrections are new assertions, not silent overwrites.
4.  **Cross-partition edges are first-class.** No forced duplication of referenced objects.
5.  **Indexes are replaceable.** No index provider gets to define global truth.
6.  **Trust is contextual and subjective.** Different applications and users may compute different reputations.
7.  **Partial knowledge is explicit.** Missing data must not be confused with false data, and an incomplete query result must not be presented as exhaustive.
8.  **Storage and computation are separable.** Users may consume somebody else's index or recommendation engine without surrendering control of their data interpretation.

There is one additional feature I'd strongly consider: **subscription dependencies**.

If you subscribe to a matching-assertion partition, your node could automatically fetch minimal identifying information for referenced movies and torrents. But it shouldn't recursively download their entire neighborhoods. Dependency depth, data size, and traversal policies should be configurable.

------------------------------------------------------------------------

## 7. The next research direction

Given your new requirements, my ranking changes significantly.

| Project | Why investigate it |
|----|----|
| <Link url="https://willowprotocol.org/" title="Willow"/> | Selective, structured peer-to-peer synchronization |
| <Link url="https://hypercore-protocol.org/" title="Hypercore"/> | Efficient replicated append-only logs |
| <Link url="https://earthstar-project.org/" title="Earthstar"/> | Distributed data with application-defined shared spaces |
| <Link url="https://www.ipfs.tech/" title="IPFS"/> | Content-addressed objects and references |
| <Link url="https://atproto.com/" title="AT Protocol"/> | Portable identities, independent indexes, custom feeds |
| <Link url="https://www.w3.org/TR/prov-o/" title="W3C PROV-O"/> | Provenance semantics for assertions |

I'd treat these as candidate building blocks, not as proven solutions to the complete problem. In particular, selective replication of arbitrary graph-query results is substantially harder than selective replication of named datasets or key ranges.

**The central research question I'd pursue is:**

*Can we design a decentralized graph protocol in which semantic subscriptions, cross-partition references, and subjective trust are native concepts, rather than application-level conventions layered onto a generic message bus?*

That seems like the genuinely novel part of your idea.

And I suspect the most useful next step would be to design a **minimal protocol for entities, assertions, partitions, and subscriptions**, then test it against your IMDb/torrent reconciliation example and a second, unrelated domain. If both work without special-case schema assumptions, we'd have a much stronger indication that the design really is generic.

## Prompt:

11/12/2026, 5:16:07 PM

# Selected text:

## Selection 1

How would your node discover this new relationship?

## My request:

yeah, i would need a way to publicly show my interest in this area, so i can receive push notifications.  
another use case is maintaining a set of software packages, for example nixpkgs, which currently is too centralized... as a user of nixpkgs, i am interested only in some packages, the package which i actually use on my computer, so i want to receive news/updates/alerts only for these packages. currently the issue tracker of nixpkgs simply contains all issues for all packages, and currently it is rather hard to get a filtered "feed of updates" only for the few relevant packages. in the use case of maintaining software packages, there is also the aspect of software security, so i want to receive security alerts for all the software i am using on my machine, so also here i need some kind of "filtered feed of updates" only for the few packages i am actually interested in...

## Response:

11/12/2026, 5:16:21 PM

This is a very good second use case, because it exposes something that the IMDb/torrent example doesn't: **subscriptions should not merely determine which data you replicate; they should also determine which future events reach you.**

And software package management adds another dimension: *dependency graphs*.

If I install package A, which depends on library B, which depends on library C, then I might want security notifications about all three, but ordinary development notifications only about A.

That suggests your system needs three distinct mechanisms:

1.  **Semantic subscriptions:** Express which objects, relationships, and event types interest me.
2.  **Dependency-aware subscriptions:** Automatically expand that interest through selected graph relationships.
3.  **Distributed notification routing:** Deliver relevant new assertions to interested nodes without making everybody download everything.

Crucially, a subscription should itself be a first-class graph object, rather than an opaque configuration setting in a particular application.

## 1. A practical example: subscribing to software packages

Suppose my computer has Firefox, VLC, and Git installed.

<box border radius="xl" padding={3} gap={3}>
  <text weight="medium">Example: software update subscriptions</text>
  {@body const [packages,setPackages] = DIL.useState(["firefox","vlc","git"])}
  {@body const [security,setSecurity] = DIL.useState(true)}
  {@body const [releases,setReleases] = DIL.useState(true)}
  {@body const [issues,setIssues] = DIL.useState(false)}
  {@body const [depth,setDepth] = DIL.useState("transitive")}
  <box gap={1}>
    <label>Installed packages</label>
    {#each [{id:"firefox",name:"Firefox"},{id:"vlc",name:"VLC"},{id:"git",name:"Git"},{id:"openssl",name:"OpenSSL"}] as p}
      <checkbox checked={packages.includes(p.id)} onChange={v=>setPackages(old=>v?[...old,p.id]:old.filter(x=>x!==p.id))} lineThrough={false}>{p.name}</checkbox>
    {/each}
  </box>
  <divider color="subtle"/>
  <box gap={1}>
    <label>Events to follow</label>
    <checkbox checked={security} onChange={setSecurity} lineThrough={false}>Security advisories</checkbox>
    <checkbox checked={releases} onChange={setReleases} lineThrough={false}>New releases and package updates</checkbox>
    <checkbox checked={issues} onChange={setIssues} lineThrough={false}>Issues and maintenance discussions</checkbox>
  </box>
  <box gap={1}>
    <label>Dependency scope</label>
    <radio-group direction="col" value={depth} onChange={setDepth}>
      <radio value="direct">Direct dependencies only</radio>
      <radio value="transitive">All transitive runtime dependencies</radio>
      <radio value="none">Selected packages only</radio>
    </radio-group>
  </box>
  <box background="surface-secondary" padding={3} radius="lg" gap={2}>
    <text weight="medium" size="xs" color="secondary">Generated subscription policy (illustrative)</text>
    <text preserveWhitespace size="xs">{`packages: [${packages.join(", ")}]
events: [${[security&&"security",releases&&"release",issues&&"issue"].filter(Boolean).join(", ")}]
dependency_scope: ${depth}
delivery: push
replication: selective`}</text>
    <button block size="sm" color="secondary" variant="outline" onClick={()=>GenUI.copy(`packages: [${packages.join(", ")}]\nevents: [${[security&&"security",releases&&"release",issues&&"issue"].filter(Boolean).join(", ")}]\ndependency_scope: ${depth}\ndelivery: push\nreplication: selective`)}><icon name="copy" inline/> Copy subscription</button>
  </box>
</box>

This is a conceptual subscription policy, not an existing service.

The really interesting feature is that the subscription isn't necessarily a static list. It can be a *query*:

> Notify me about security vulnerabilities affecting any component in the dependency closure of my current system configuration, including packages introduced by future updates.

When my system configuration changes, the subscription's effective target set changes automatically.

## 2. Something very relevant already exists in NixOS

Interestingly, the NixOS community has already built a specialized system addressing part of your exact problem.

<row align=start gap={3}>
  <AsyncImage query="NixOS snowflake logo" aspectRatio="1:1" maxWidth="90px"/>
  <box flex="1" gap={1}>
    **<Link url="https://tracker.security.nixos.org/" title="Nixpkgs Security Tracker"/>**

    <text color="secondary" size="xs">Open-source · NixOS security infrastructure</text>

    This project automatically matches CVE records against Nixpkgs derivations, lets humans review suggested matches, and supports package-specific vulnerability notifications. <Cite refs={["turn688621search0","turn688621search1"]}/>

  </box>
</row>

This is particularly striking because it combines several things from your original idea:

- Automatic entity reconciliation between independent databases.
- Human review of proposed matches.
- Tracking which packages are affected by which vulnerabilities.
- Publishing actionable security information.
- Notifying users and maintainers interested in particular packages.

Its source code is at <Link url="https://github.com/NixOS/nix-security-tracker" title="NixOS/nix-security-tracker"/>.

I would seriously study its data model and workflow. It could serve as an excellent real-world reference implementation for one domain of your universal graph.

However, it's still a specialized centralized service, not the decentralized, arbitrary-entity subscription protocol you're envisioning.

## 3. Publish interests, not just data

Your suggestion to *publicly announce your interest* leads to an important distinction between three kinds of objects:

| Object           | Purpose                                                |
|------------------|--------------------------------------------------------|
| **Assertion**    | "Package X is affected by vulnerability Y."            |
| **Subscription** | "I want to know about vulnerabilities affecting X."    |
| **Notification** | "A new relevant assertion is available at location Z." |

All three could be independently signed and published.

A subscription could include a predicate, an identity or pseudonym, a notification endpoint, an expiration time, and a preferred delivery method.

The subscription doesn't have to reveal your entire installed software inventory. That would be undesirable from a security perspective.

Instead, you might publish interest in broad topics to a relay, maintain fine-grained filters privately, or use a trusted notification provider. More advanced designs could explore private information retrieval or encrypted subscriptions, although those introduce substantial complexity.

### Push versus pull

I wouldn't make the system push-only.

A robust design would combine:

**Push for latency:** A relay notifies your node when it discovers a potentially relevant assertion.

**Pull for correctness:** Your node periodically reconciles its state with subscribed publishers or indexes to recover missed notifications.

**Signed data for integrity:** The notification points to an independently verifiable assertion. The relay need not be trusted to author the underlying claim.

That avoids making reliable delivery dependent on a permanently online subscriber.

It also suggests using durable cursors or sequence numbers, so reconnecting clients can efficiently request events missed while offline.

## 4. The important complication: package identity and versioning

For software security, simply subscribing to a package name isn't enough.

Consider these distinct entities:

<box border radius="lg" padding={3} gap={2}>
  <box align=center gap={1}>
    <box background="surface-secondary" radius="md" padding={2} width="85%" align=center>
      **Upstream project: OpenSSL**
    </box>
    <icon name="arrow-down" color="tertiary"/>
    <grid columns={2} gap={2}>
      <grid-item>
        <box background="surface-secondary" radius="md" padding={2} align=center>
          <text weight="medium" size="sm">Upstream release</text>
          <text size="xs" color="secondary">Version 3.x</text>
        </box>
      </grid-item>
      <grid-item>
        <box background="surface-secondary" radius="md" padding={2} align=center>
          <text weight="medium" size="sm">Nixpkgs package</text>
          <text size="xs" color="secondary">Patch set / revision</text>
        </box>
      </grid-item>
    </grid>
    <icon name="arrow-down" color="tertiary"/>
    <box background="surface-secondary" radius="md" padding={2} width="85%" align=center>
      **Installed derivation / store path**
    </box>
    <icon name="arrow-down" color="tertiary"/>
    <box background="surface-secondary" radius="md" padding={2} width="85%" align=center>
      **Your system generation**
    </box>
  </box>
  <caption>Conceptual identity layers, not a literal one-to-one package dependency chain.</caption>
</box>

A vulnerability may affect an upstream version but not the corresponding Nixpkgs derivation because a security patch was backported.

Conversely, the vulnerability may affect a transitive dependency you never installed explicitly.

Therefore, a useful security feed should answer:

- Is this vulnerability relevant to my *exact installed build*?
- Is it already patched in my Nixpkgs revision?
- Is a fixed build available in my channel?
- Does it affect a runtime dependency or only a build-time dependency?
- Is the affected component actually used by the software I run?

That requires more than matching package names. It requires a graph of software projects, versions, derivations, dependencies, patches, advisories, and deployments.

For external vulnerability sources, <Link url="https://osv.dev/" title="OSV"/> is worth studying. Its API supports querying vulnerabilities by package/version and batching multiple queries. <Cite ref="turn688621search4"/>

But mappings between upstream packages, Nixpkgs derivations, and actual installed builds still require careful handling.

## 5. The larger architectural insight: subscriptions are graph queries over time

I think this is the most important generalization.

Your original system asked:

*Which entities and assertions should I download?*

Your new requirement asks:

*Which future changes to the global graph should I learn about?*

Those are two versions of the same problem.

A subscription can be understood as a continuously evaluated graph query:

``` math
S(t)=Q(G(t),P(t))
```

where:

- $`G(t)`$ is the discoverable graph at time $`t`$.
- $`P(t)`$ is the subscriber's current policy and local context.
- $`Q`$ is a graph query selecting relevant assertions.
- $`S(t)`$ is the resulting set of relevant assertions.

The notification system detects changes in $`S(t)`$, not merely newly published messages.

This distinction matters. A vulnerability advisory published last month could become relevant *today* because you installed a newly affected package or because someone corrected an erroneous package mapping.

So the system needs to detect changes caused by both **new data and changes in interpretation or subscription context**.

That is a much more general abstraction than conventional RSS feeds, GitHub notifications, or Nostr event filters.

## 6. How I would implement this incrementally

<list marker="number" connector="solid" gap={2}>
  <list-item>
    **Local software inventory**

    Generate a machine-readable inventory from the active NixOS system and selected profiles. Represent package identities, exact derivations, and runtime dependencies.

  </list-item>
  <list-item>
    **Import external assertions**

    Ingest Nixpkgs issues, pull requests, package updates, security tracker entries, and vulnerability advisories as independently attributable events.

  </list-item>
  <list-item>
    **Resolve identities**

    Match external references to local package identities, preserving uncertainty and provenance.

  </list-item>
  <list-item>
    **Evaluate semantic subscriptions**

    Compute relevant changes using package identities, dependency relationships, event types, and user-defined filters.

  </list-item>
  <list-item>
    **Federate publishers and indexes**

    Allow independent servers to publish assertions and advertise which semantic topics they index. Add push notifications and periodic reconciliation.

  </list-item>
</list>

This would already be useful as a standalone open-source NixOS tool, even before developing a universal decentralized protocol.

And it could provide an unusually good test case for the bigger vision: software security is unforgiving of bad entity matches, incomplete information, and unreliable notification delivery.

------------------------------------------------------------------------

## 7. One architectural question I'd investigate next

**Should subscriptions be public graph objects, or should only their routing information be public?**

These lead to different designs.

A fully public subscription allows anybody to discover that Alice is interested in package X and send relevant information directly.

A private subscription with public routing hints allows relays to deliver potentially relevant events without exposing the full interest graph.

A hybrid model might allow users to publish broad interests publicly while keeping exact installed-package lists and sensitive trust policies local.

I lean strongly toward the hybrid model. In the NixOS example, a publicly readable inventory of installed packages could help attackers identify vulnerable machines.

There's also a potentially useful new abstraction here: **a subscription could be treated as a materialized, continuously maintained subgraph**. Nodes would then synchronize only the portions of that subgraph they need, with notifications describing incremental changes.

That would unify your requirements for selective replication, cross-partition graph relationships, software updates, security alerts, and personalized social feeds under one architectural concept.

And that, to me, is a stronger foundation for your "connect all the dots" project than starting from either a traditional semantic-web database or a generic social messaging protocol.

## Response:

11/12/2026, 5:16:27 PM

------------------------------------------------------------------------

Powered by [ChatGPT Exporter](https://www.chatgptexporter.com)
