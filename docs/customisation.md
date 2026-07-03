# Customising the OpenClaw ESP32-S3-Box-3 firmware

This fork is based on `esphome/wake-word-voice-assistants`, the ESPHome Web Tools firmware source for Home Assistant voice devices.

The OpenClaw/Marvin variant lives in:

```text
openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.yaml
openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.factory.yaml
openclaw-assets/*.png
wake-word-models/
```

## Display images

The display state images are controlled by substitutions near the top of the YAML:

```yaml
loading_illustration_file: https://github.com/.../openclaw-assets/loading_320_240.png
idle_illustration_file: https://github.com/.../openclaw-assets/idle_320_240.png
listening_illustration_file: https://github.com/.../openclaw-assets/listening_320_240.png
thinking_illustration_file: https://github.com/.../openclaw-assets/thinking_320_240.png
replying_illustration_file: https://github.com/.../openclaw-assets/replying_320_240.png
error_illustration_file: https://github.com/.../openclaw-assets/error_320_240.png
timer_finished_illustration_file: https://github.com/.../openclaw-assets/timer_finished_320_240.png
```

To personalise the assistant, replace the PNG files in `openclaw-assets/` with 320×240 PNGs and keep the filenames, or change the substitution URLs.

## Wake words

The starter YAML keeps the known-good built-in models:

```yaml
micro_wake_word:
  id: mww
  task_stack_in_psram: true
  models:
    - model: okay_nabu
      sliding_window_size: 3
      probability_cutoff: 97%
    - hey_mycroft
    - hey_jarvis
```

For a custom wake word, train a microWakeWord model, place the JSON/TFLite files under `wake-word-models/`, and add a model reference:

```yaml
    - model: github://darrenjrobinson/openclaw-wake-word-voice-assistants/wake-word-models/marvin.json@main
```

Keep `hey_jarvis` available until the custom phrase has been tested in the target room. Reality has a sense of humour and it expresses itself through false rejects.

## Wake-word restart latency

The upstream ESP32-S3-Box-3 YAML already waits for announcements and speaker playback before restarting on-device microWakeWord in `voice_assistant.on_end`.

If you still see a post-response dead zone:

- Verify the device is running current ESPHome and the 240 MHz CPU setting.
- Keep `task_stack_in_psram: true` enabled.
- Try `sliding_window_size: 3` with a high cutoff such as `97%`.
- Keep custom display code lightweight.

## Build / adopt path

During development, import this YAML into ESPHome Dashboard:

```text
github://darrenjrobinson/openclaw-wake-word-voice-assistants/openclaw-esp32-s3-box-3/openclaw-esp32-s3-box-3.yaml@main
```

The factory YAML is for ESP Web Tools / release builds once the firmware artefact publishing path is wired up.
