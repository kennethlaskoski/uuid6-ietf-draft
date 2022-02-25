# Updates

#### Draft 03 is in progress for an estimated submission of 31 March 2022
- HTML: https://uuid6.github.io/uuid6-ietf-draft/
- Text: https://raw.githubusercontent.com/uuid6/uuid6-ietf-draft/master/draft-peabody-dispatch-new-uuid-format-03.txt

#### Draft 02 was submitted 07 October 2021: 
- HTML: https://www.ietf.org/archive/id/draft-peabody-dispatch-new-uuid-format-02.html
- Text: https://www.ietf.org/archive/id/draft-peabody-dispatch-new-uuid-format-02.txt

---

# New UUID Formats
This is the GitHub repo for the IETF draft surrounding the topic of new UUID formats.
Various discussion will need to occur to arrive at a standard and this repo will be used to collect and organize that information.

## High Level Overview
1. **UUID version 6**: A re-ordering of UUID version 1 so it is sortable as an opaque sequence of bytes. Easy to implement given an existing UUIDv1 implementation.
  - `time_high|time_mid|time_low_and_version|clk_seq_hi_res|clk_seq_low|node`
2. **UUID version 7**: An entirely new time-based UUID bit layout sourced from the widely implemented and well known Unix Epoch timestamp source.
  - `unix_ts_ms|rand_a|var_ver|rand_b`
3. **UUID version 8**: A free-form UUID format which has no explicit requirements except maintaining backward compatibility.
 - `custom_a|var_ver|custom_b`

---

# RFC Scope
In order to keep things on track the following topics have been decided as in-scope or out of scope for this particular RFC.
For more information on any of these items refer to the XML, TXT, HTML draft, research and the issue tracker for a particular discussion (follow hyperlinks below.)

### In Scope Topics - UUID Generation
- [Timestamp Granularity](https://github.com/uuid6/uuid6-ietf-draft/issues/23)
   - Sub-Topics: Timestamp epoch source, format, length, accuracy and bit layout
- [Monotonicity and Counters for same Timestamp-tick collision avoidance during batch UUID creation](https://github.com/uuid6/uuid6-ietf-draft/issues/60)
   - Sub-Topics: Counter position, length, rollover handling and seeding.
- [Pseudo-random formatting, length and generation methods](https://github.com/uuid6/uuid6-ietf-draft/issues/55)
- [Version and Variant Bit Usage](https://github.com/uuid6/uuid6-ietf-draft/issues/26)
- Distributed UUID Generation best practices
  - Sub-Topics: [Shared Knowledge Schemes and embedded nondescript node identifiers](https://github.com/uuid6/uuid6-ietf-draft/issues/36) 

### In Scope Topics - UUID Best Practices as it relates to the previous topics
- Global and Local Uniqueness (collision resistance mechanisms)
- Unguessability
- Sorting/Ordering techniques
- Storage and Opacity best practices
- Big Endian vs Little Endian bit layout
- Any and all UUID security concerns!
  - Sub-Topics: [MAC address usage in next-generation UUIDs](https://github.com/uuid6/uuid6-ietf-draft/issues/13)

---

### Topics being scoped
- [Alternative text encoding techniques (Crockfords Base32, Base64, etc)](https://github.com/uuid6/uuid6-ietf-draft/issues/2)

---

### Out of Scope Topics (as as the result of discussion threads)
- [Variable length subsecond precision encoding](https://github.com/uuid6/uuid6-ietf-draft/issues/24)
- [Variable length UUIDs](https://github.com/uuid6/uuid6-ietf-draft/issues/59) [Tabled for a future RFC Draft]

### Out of Scope Topics (for backwards compatibility)
- Changing the default 8-4-4-4-12 UUID text layout
- Changing anything about RFC4122's UUID versions 1 through 5
- [Changing too much about UUIDv6 that would otherwise inhibit porting v1 to v6](https://github.com/uuid6/uuid6-ietf-draft/issues/52)

---

# Contributing
- The XML draft in the root folder is the most recent working draft for re-submission to the IETF.
  - An HTML and Textual (.txt) RFC representation will be provided in the root folder to ease reader input and discussion.
  - [Older drafts](https://github.com/uuid6/uuid6-ietf-draft/tree/master/old%20drafts) are available for view here or on the [IETF Datatracker](https://datatracker.ietf.org/doc/draft-peabody-dispatch-new-uuid-format/).
- The RFC Draft utilize an XML formatted document that follows [RFC7742 markup](https://xml2rfc.tools.ietf.org/rfc7749.html). All XML changes MUST follow this format and pass conversion to `.txt` and `.html` via https://xml2rfc.tools.ietf.org/
- Utilize the issue tracker to discuss topics, solutions, problems, typos and anything else.
  - Where possible contribute to an existing [Discussion Thread](https://github.com/uuid6/uuid6-ietf-draft/issues?q=is%3Aissue+is%3Aopen+label%3ADiscussion) vs creating a new thread.
  - Reviewing is the pre-Draft 01 [Research efforts](https://github.com/uuid6/uuid6-ietf-draft/tree/master/research) is encouraged before diving into discussion threads.
  - New threads that propose alternative text should utilize `Proposed Draft Change` GitHub issue template proper information is captured for the draft authors.
  - Be civil!
- Pull requests will be accepted  *as long as the text is concise, clear and objective.* 
  - PRs will not be accepted for changes to the decision made for the draft without full discussion. 
  - PRs MUST include the updated `.xml` and xml2rfc generated `.txt` and `.html` documents.
  - Draft versions are frozen until submission to the IETF; at which point new work constitutes a new draft version.

---

# Prototyping
Remember first and foremost that this specification is still a draft. Breaking changes are to be expected. Prototypes SHOULD only be implemented to verify or discredit topics of the draft text.
- [Prototype Implementations](https://github.com/uuid6/prototypes) are available via this repro.