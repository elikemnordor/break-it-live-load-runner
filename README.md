# Break It Live Linux diagnostic runner

This public repository contains only the GitHub Actions instructions used to run
bounded load diagnostics on a standard GitHub-hosted Ubuntu runner.

The application source remains in the private `elikemnordor/break-it-live`
repository. The workflow checks it out with a read-only deploy key, runs the
Cloudflare Worker locally inside the runner, and prints the diagnostic report to
the job log. It does not deploy or send traffic to Cloudflare.

The workflow is manual-only and offers two fixed profiles:

- `local-1000`: initial Linux runner validation.
- `local-2500`: staged 1,500 → 2,000 → 2,500 concurrent-client diagnostic.
