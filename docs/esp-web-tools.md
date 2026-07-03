# ESP Web Tools / factory image path

This fork was created from the ESPHome wake-word voice assistant firmware source used by ESP Web Tools:

- Upstream source: https://github.com/esphome/wake-word-voice-assistants
- Upstream install flow: ESPHome + ESP Web Tools
- OpenClaw target YAML: `openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.yaml`
- OpenClaw factory YAML: `openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.factory.yaml`

## Development path

For now, the recommended customisation path is ESPHome Dashboard import:

```text
github://darrenjrobinson/openclaw-wake-word-voice-assistants/openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.yaml@main
```

That lets a user adopt the device and customise images, wake-word models, substitutions, and ESPHome options in their own dashboard.

## Factory / ESP Web Tools path

The repository includes a GitHub Actions build workflow for the OpenClaw ESP32-S3-Box-3 factory YAML. On a GitHub release, the build workflow should compile and upload firmware artefacts to the release.

A polished ESP Web Tools installer page can be added later once the release artefact names and manifest URL are confirmed from the first successful release build.

## Update manifest note

The factory YAML has an `update.source` placeholder pointing at a future hosted manifest location. Until a stable firmware hosting path is wired up, dashboard import is the safer supported route.

Do not publish personal Wi-Fi credentials, Home Assistant tokens, or OpenClaw tokens in any factory image.

## Initial repository publishing note

The initial OpenClaw firmware source repository publishes the ESPHome YAML, assets, and documentation first. Active GitHub Actions firmware build workflows are intentionally not enabled in the first commit. Add them once the repository token has workflow-write permission and the desired release artefact names/manifest URLs are confirmed.
