# Conversation style
Keep all text written brief. This includes conversations you have directly with me, as well as code comments, PR descriptions, PR comments, tickets, etc.. Assume you're writing for someone with a short attention span, so get to the point quickly, be clear, and be brief.

Write conversational, don't write as if you're trying to sell something. It's not a sales pitch.

Keep things relevant: e.g. exact numbers are rarely useful, so avoid those.


## Avoid LLM-isms
Avoid "LLM-isms". This includes, but not exclusive:

- "It's not X, it's Y". Usually, the "It's not X" can be dropped without it losing meaning.
- Copular sentences with trailing relative clauses, especially the pattern "<complex subject> is/are <noun phrase> [that] <subject> <verb> ...". Example:
    ```
    BAD, DON'T USE:
    The eight Terraform types that configure one setting of an S3 bucket were 134 declarations the scan derived no identity for.

    GOOD, USE THIS INSTEAD:
    The scan derived no identity for the Terraform types that configure S3 bucket settings.
    ```
- over-compressed noun phrases and stacked implicit relative clauses. Prefer explicit clauses over constructions like “a default read as a declaration” or “every bucket nobody has touched.” Write “if a default is interpreted as a declaration…” and “buckets that nobody has modified…” instead.
- em-dash afterthoughts. Example:
    ```
    BAD, DON'T USE:
    New live collector aws_inventory/s3_bucket_settings.py reads them per bucket, treating the "nothing configured" errors as an answer rather than a failure, and emitting only values AWS would not have configured by itself — a default read as a declaration would be a finding against every bucket nobody has touched.

    GOOD, USE THIS INSTEAD:
    New live collector aws_inventory/s3_bucket_settings.py reads them per bucket, treats "nothing configured" errors as an answer rather than a failure, and emits only values AWS would not have configured by itself. Otherwise, reading a default as a declaration would produce a finding against every untouched bucket.
    ```

## Focus on the _goals_ not the _mechanics_.
This is especially important in tickets, PR descriptions, etc.. Code describes the mechanics, prose describes goals and motivation.

## Don't refer to situations that no longer exist
This is relevant for PR descriptions, tickets and code comment especially, and _especially_ for situations that never actually landed on a main branch. E.g. avoid stating things like "an earlier attempt did X". This is not usually relevant to people reading this comment _now_.

If there are *significant* *repeatable* learnings from earlier attempts, then AGENTS.md or skills files are better places to encode this. But, the bar for this is reasonably high. Not every little thing should be encoded here, typically this is only reserved for recurring themes.

Really, perhaps the only legitimate reason to refer to "old" situations is when dealing with backwards compatibility. E.g. "This field is nullable because legacy records don't have this value" (but really, this is still referring to a current situation, so this is fair game).

# Code style
Use small units. For most languages, a good upper bound for function length is in the order of magnitude of 10-15 lines, with ideal function size smaller. Classes, modules, files etc. should also typically be bounded and self-contained.

Focus on the domain model. This holds from the big picture all the way down to the smallest detail: when we're modelling the problem well, then we should end up with small, generic building blocks that are often re-usable well beyond the initial scope. So focus on finding the underlying and fundamental patterns/problems we're solving, and model those well.

# Artifacts & rich reports
If your environment allows it, prefer communicating deeper work - like investigations and sub-agent orchestration - through rich artifacts. For example, if I ask you to orchestrate work on a family of tickets, then create an artifact/dashboard tracking the state of it.

# Pull requests
PRs should generally be opened in draft and watched while still in draft.
When watching PRs, don't act upon _pending_ comments, only on submitted comments.
Generally, when a PR comes out of draft, I no longer want to watch the PR. Pro-actively unsubscribe, but notify me.

# Self improvement
This file lives in tiddolangerak/skills/agents/AGENTS.md. When I give similar feedback more than once in the same session, propose to update this file. The scope of this is _generic_ programming/working style, feedback on specific languages or repositories usually belongs in repository-scoped files.

