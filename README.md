# Concertje

Find concerts and gigs in Belgium and the Netherlands from a conversation with Claude.

## Install

On claude.ai, add it from the directory under **Customize > Plugins**. In Claude Code:

```
/plugin install concertje --marketplace kevinmeyvaert/concertje-claude-plugin
```

## Use it

Connect the Concertje connector from the plugin's Connectors tab and sign in with your Concertje
account. Then ask what's on in a city or at a venue, whether an artist is touring here, or whether a
show is sold out: "Any post-punk shows in Antwerp this weekend?" Claude searches Concertje, filters by
date, city, venue or genre, and shows the concerts as cards with the date, venue, ticket status and
price, each linking to its page on concertje.be.

The `find-concerts` skill teaches Claude which tool to use for each question, how to pick Belgium or
the Netherlands, and to show the final list once.

## Data

The plugin sends your search terms (artist, city, venue, genre, dates) to Concertje through
ai.concertje.be, signed in with your Concertje account. It is read-only: it can't buy tickets or change
anything in your account. See https://concertje.be/privacy.
