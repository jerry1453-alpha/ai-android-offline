# GPU / NDK / Android build notes

This project is designed for Android local AI inference powered by a GGUF model.

Recommended stack:
- Kotlin Android app
- CMake + NDK for native integration
- llama.cpp / GGML for local model inference in native code
- Android Studio or GitHub Actions for build

Target device family:
- Xiaomi 10 Pro and other arm64-v8a devices

Model recommendation:
- Use a quantized GGUF model such as a 7B q4_k_m model for a practical balance between quality and on-device performance.
- Smaller models (3B) are more portable and faster; larger models require more RAM and time.

Model placement:
- Place the model file in the device's external storage or app-specific files directory
- Example path: `/storage/emulated/0/Android/data/com.example.aioffline/files/models/model.gguf`
- Or copy it into `app/src/main/assets/models/` if you want to bundle it with the APK (not recommended for large models)

Important:
- Large model files are not committed to source control.
- Keep the app logic generic so you can swap in another GGUF model later.
