# Carried patches

Patches on top of v1.27.2. Each patch has a corresponding upstream issue.

- wti: expose save_live_blob query param on /run_live endpoint (upstream: https://github.com/google/adk-python/issues/4707)

## Making changes

- One fix per commit, prefixed `wti:` (e.g. `wti: fix live author attribution`)
- Update this file with each patch and its upstream PR number
- Open an upstream PR on `google/adk-python` for every patch
- Do not reformat or refactor upstream code — keep diffs minimal

## Rebasing on a new upstream release

    git fetch upstream --tags
    git rebase <new-tag>
    # drop patches merged upstream, resolve conflicts
    git tag wti/patches-on-<new-tag>
    git push --force-with-lease origin wti/patches
    git push origin wti/patches-on-<new-tag>

Then in the consuming repo: `uv lock --upgrade-package google-adk`
