# GitHub Actions

Active firmware build workflows are intentionally not enabled in the initial public source commit.

The upstream ESPHome repository uses GitHub Actions to build factory binaries on release. Add an active workflow later once repository credentials include GitHub Actions workflow write permission and the release artefact names have been verified.

See `docs/esp-web-tools.md`.


Dependabot is also disabled for now because there are no active workflows to update. Re-enable `.github/dependabot.yml` together with active firmware build workflows.
