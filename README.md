# OpenClaw Wake Word Voice Assistants

OpenClaw/Marvin-customised fork of the ESPHome wake-word voice assistant firmware sources.

Upstream: https://github.com/esphome/wake-word-voice-assistants

This fork starts with the ESP32-S3-Box-3 Home Assistant voice assistant image flashed via ESP Web Tools, then layers an OpenClaw/Marvin customisation path on top:

- custom display assets for assistant states
- a safe place for custom microWakeWord model files
- documentation for personalising the wake word and screen identity
- ESPHome YAML suitable for dashboard import and later factory builds

## Current target

```text
openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.yaml
```

This is based on upstream:

```text
esp32-s3-box-3/esp32-s3-box-3.yaml
```

## Import into ESPHome Dashboard

Use this package URL:

```text
github://darrenjrobinson/openclaw-wake-word-voice-assistants/openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.yaml@main
```

## Customisation docs

See:

- [docs/customisation.md](docs/customisation.md)
- [docs/esp-web-tools.md](docs/esp-web-tools.md)
- [wake-word-models/README.md](wake-word-models/README.md)

## Relationship to the OpenClaw Home Assistant bridge

The conversation bridge lives separately at:

https://github.com/darrenjrobinson/openclaw-voice-assistant

The expected end-to-end path is:

```text
ESP32-S3-Box-3
  → Home Assistant Assist pipeline
  → OpenClaw Conversation AlfredPatch
  → OpenClaw agent
  → MCPorter `ha`
  → ha-mcp
  → Home Assistant
```

## Safety

Do not commit Wi-Fi credentials, Home Assistant tokens, OpenClaw tokens, or private URLs. This repo should remain safe for public firmware-source sharing.

## License

This fork retains the upstream Apache-2.0 license.
