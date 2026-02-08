# Robbie Voice Assistant - ESP32-S3-Box-3

Direct voice interface to OpenClaw (Robbie), bypassing Home Assistant Assist pipeline.

## Architecture

```
┌─────────────────────────┐
│   ESP32-S3-Box-3        │
│   ├─ micro_wake_word    │──► "Hey Robbie" (on-device)
│   ├─ esp_adf mic        │
│   └─ Display            │
└───────────┬─────────────┘
            │ WebSocket / HTTP
            ▼
┌─────────────────────────┐
│   VPS (robbie.openclaw) │
│   ├─ Audio receiver     │
│   ├─ Whisper STT        │
│   ├─ OpenClaw inject    │
│   └─ HA TTS trigger     │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│   Home Assistant        │
│   └─ Living Room Speaker│
└─────────────────────────┘
```

## Components

1. **esp32-s3-box-3.yaml** - ESPHome firmware config
2. **custom_components/robbie_voice/** - Custom component for audio streaming
3. **vps/robbie-voice-server/** - VPS-side receiver + processor

## Status

- [ ] ESPHome base config
- [ ] Custom audio streaming component
- [ ] VPS WebSocket server
- [ ] Whisper integration
- [ ] OpenClaw integration
- [ ] HA TTS integration
- [ ] OTA deployment
