# 646 transcript timer

This repository contains only a timer workflow. No application code, caller data, audio, or credentials are stored here.

The workflow uses the standard Ubuntu GitHub-hosted runner for a public repository. It calls a protected endpoint every five minutes, offset from the top of the hour. The application checks authentication, limits requests, and processes at most one eligible 646 job. Historical jobs remain excluded.

Configuration lives in repository secrets `KOLLEL646_DRAIN_URL` and `KOLLEL646_DRAIN_TOKEN`. The application holds the matching token in its private secrets. Set repository variable `KOLLEL646_DRAIN_ENABLED` to `true` to enable the timer. Delete that variable or disable the workflow to stop it.

The workflow has no repository permissions, performs no checkout, uses no third-party actions, and logs only the HTTP status. GitHub schedules can be delayed or skipped under load, so this is not an exact five-minute delivery guarantee. GitHub may disable public-repository schedules after 60 days without repository activity; they then need re-enabling.
