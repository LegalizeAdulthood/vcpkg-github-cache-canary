<!--
SPDX-License-Identifier: GPL-3.0-only

Copyright 2026 Richard Thomson
-->

# vcpkg GitHub Cache Canary

This repository is a tiny external consumer for
`LegalizeAdulthood/vcpkg-github-cache`.

It exists to verify behavior that `uses: ./` integration tests cannot prove:

- action resolution by tag or commit SHA;
- caller repository `GITHUB_TOKEN` package permissions;
- GitHub Packages restore and upload behavior from a separate repository;
- analyzer summaries and artifacts as users see them.

The project builds one executable that links `fmt` from vcpkg.  The canary
workflow writes a dedicated triplet so the package names are easy to identify
in GitHub Packages.

## Testing a Candidate

Edit `.github/workflows/canary.yml` and replace both `@v1` action refs with
the candidate commit SHA or release tag under test.  Keep the setup and
analyze refs in sync.

Then push the branch or run the workflow manually.

