# Break It Live Linux diagnostic runner

This public repository contains only the GitHub Actions instructions used to run
bounded load diagnostics on a standard GitHub-hosted Ubuntu runner.

The application source remains in the private `elikemnordor/break-it-live`
repository. The workflow checks it out with a read-only deploy key and prints
the diagnostic report to the job log. Local profiles run the Cloudflare Worker
inside the runner and never contact staging. The fixed staging profile targets
the existing staging Worker with access codes stored as encrypted repository
secrets; it does not deploy or modify Worker configuration.

The workflow is manual-only and offers three fixed profiles:

- `local-1000`: initial Linux runner validation.
- `local-2500`: staged 1,500 → 2,000 → 2,500 concurrent-client diagnostic.
- `staging-2500`: the same staged 2,500-client profile against the deployed
  Cloudflare staging Worker, using access codes stored as GitHub Actions
  secrets.
