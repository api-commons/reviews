# Reviews

The common reviews vocabulary -- the reviews customers write, the replies businesses post, the business locations being reviewed and the review requests that ask for them -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Reviews, Ratings, Reputation Management, Customer Reviews, Online Reviews, Review Management, User-Generated Content in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| review | 26 | 22 | rating 68%, created_at 64%, id 64%, body 55%, author_name 50% | reviews 24, review 6 |
| review_reply | 7 | 6 | body 67% | responses 3, reply 3, comments 1 |
| reviewed_location | 8 | 7 | name 71%, address 57%, city 57%, description 57%, metadata 57%, phone 57% | locations 7, location 2, business 1 |

Cohort: 42 providers with harvested OpenAPI, 26 crosswalks. Of the providers exposing a review: 35% create, 85% list, 38% fetch, 4% update, 0% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A review agrees on rating, body, author, id and created_at across reputation platforms, product-review tools and listing networks: the review is one of the most uniform user-generated resources in the commons.
- A reply agrees on its body; the author and timestamps are carried by too few to share.
- A reviewed location agrees on name, address, city, phone and description.

## Measured against the standard

The census reads what providers publish. Where the domain has a standard, the standard's own
definition is read as one more voice: how much of the measured core it defines, and what it
defines that no provider in the cohort publishes. Crosswalks are in [standards/](standards).

| Standard | Concept | Core defined by the standard | Fields only the standard has |
| --- | --- | ---: | ---: |
| [schemaorg-30.1](https://github.com/schemaorg/schemaorg/tree/v30.1) | `review` | 60% | 123 |

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Ratings and feedback count as reviews only beneath products, reviews or locations; bare `/ratings` is a credit or app rating elsewhere.
- Replies cover responses and comments beneath a review.
- Review locations are `/review-locations`: `/locations` is a store, a work site or a restaurant in other contexts.
- Review requests were measured and dropped (1 provider).

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
