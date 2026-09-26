# Privasys Contributor Licence Agreements

Before we merge a contribution to a Privasys project, we ask its author to
accept a Contributor Licence Agreement (CLA). This repository holds the
agreements, the record of who has accepted them, and the check that runs on
pull requests.

- [Individual Contributor Licence Agreement v1.0](individual-cla.md), for
  people contributing in their own name.
- [Entity Contributor Licence Agreement v1.0](entity-cla.md), for companies,
  universities and other organisations whose staff contribute as part of their
  work.

## What the agreement says

- **You keep your copyright.** The agreement is a licence, not an assignment,
  and you remain free to use your work however you like.
- **Privasys may also license your contribution under other terms.** Our
  products are published under the AGPL-3.0. The agreement lets Privasys offer
  them under other licences too, for example commercial ones, with your work
  included.
- **Your contribution stays open source.** For as long as Privasys distributes
  your contribution, we keep it available to the public under the licence the
  project had when you contributed, or another licence approved by the Open
  Source Initiative (section 4).
- **A patent licence** for the patents your contribution necessarily
  infringes, on the same terms as the Apache Licence 2.0.
- It is governed by the law of England and Wales.

The agreements are based on the Apache Software Foundation's individual and
corporate CLAs, with section 4 added.

## How to sign

**As an individual**, when you open your first pull request, a check will ask
you to post this sentence as a comment on it:

```
I have read the Privasys Contributor Licence Agreement v1.0 and I accept it.
```

That is all. It covers every Privasys repository, so you only do it once. If
you would rather sign before contributing, or have contributed before the
check existed, send the same sentence with your full name and GitHub account
to contact@privasys.org.

**As an organisation**, complete the signature block and Schedule A of the
[entity agreement](entity-cla.md) and send the signed copy to
contact@privasys.org. The people listed in Schedule A are then covered on every
pull request, with nothing to post.

## The record

Signatures are kept on the [`signatures`](../../tree/signatures) branch,
matched on the numeric GitHub account id (it survives a change of username):

| File | Content | Written by |
|---|---|---|
| `v1/individuals.json` | Individual signatures: account, date, and the comment or email | the check, or a maintainer for email signatures |
| `v1/entities.json` | Signed entity agreements and their Authorised Contributors (no personal data beyond GitHub accounts; the signed copies are kept in company records) | a maintainer |
| `exempt.json` | Privasys staff, whose work belongs to Privasys as their employer | a maintainer |

A new version of an agreement gets a new folder (`v2/`), and everyone accepts
it again.

## For maintainers: adding the check to a repository

Copy [templates/cla.yml](templates/cla.yml) to `.github/workflows/cla.yml`. It
calls [the check](.github/workflows/check.yml), which runs on every pull
request and on comments that accept the agreement or say `recheck`. The check
reads the pull request's commits through the API and never runs its code.

The organisation secret `CLA_SIGNATURES_TOKEN` must be available to the
repository. It is a fine-grained token with *Contents: read and write* on
`Privasys/cla` only.

To make the check required, add a ruleset on `main` that requires the
`Contributor Licence Agreement` status from GitHub Actions, with the
repository admin role as a bypass actor. The check only runs on pull requests,
so without the bypass a direct push to `main` would be rejected for lacking the
status.

## Licence

The check and the template are under the [MIT licence](LICENSE).
