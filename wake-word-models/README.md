# Custom wake-word models

Place custom microWakeWord model manifests and `.tflite` files here.

ESPHome accepts model references in several forms, including:

```yaml
micro_wake_word:
  models:
    - model: github://darrenjrobinson/openclaw-wake-word-voice-assistants/wake-word-models/marvin.json@main
```

A model manifest is a JSON file that points to the trained TFLite file and declares metadata such as `wake_word`, `probability_cutoff`, `sliding_window_size`, and `tensor_arena_size`.

Training notes:

- ESPHome uses the `microWakeWord` framework.
- Start with server-side wake-word experiments if you are still testing phrases.
- Once a phrase performs well, train a microWakeWord model and add the JSON/TFLite pair here.
- Tune `sliding_window_size` and `probability_cutoff` for the target device and room noise.

References:

- https://esphome.io/components/micro_wake_word/
- https://github.com/kahrendt/microWakeWord
- https://github.com/esphome/micro-wake-word-models
