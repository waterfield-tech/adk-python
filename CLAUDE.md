# ADK Python Fork

This is Waterfield Tech's fork of `google/adk-python`. It carries targeted
bug fixes for live audio sessions on the `wti/patches` branch.

See `PATCHES.md` for the current list of patches and their upstream issue links.

## Conventions

- One fix per commit, prefixed `wti:` (e.g. `wti: fix live author attribution`)
- Do not reformat or refactor upstream code — keep diffs minimal
- Every patch should have a corresponding upstream issue or PR on `google/adk-python`
- Update `PATCHES.md` when adding or removing patches

## Rebasing on a new upstream release

```bash
git fetch upstream --tags
git checkout wti/patches
git rebase <new-tag>
# drop patches merged upstream, resolve conflicts
git tag wti/patches-on-<new-tag>
git push --force-with-lease origin wti/patches
git push origin wti/patches-on-<new-tag>
```

Then in the consuming repo (`adk-agents`): `uv lock --upgrade-package google-adk`

## Upstream contribution

Follow `CONTRIBUTING.md` (Google CLA required). Create PRs from clean branches
off `upstream/main`, not from `wti/patches`. See the upstream issue linked in
each patch entry in `PATCHES.md`.

## Testing

```bash
uv sync --all-extras
pytest ./tests/unittests
```
