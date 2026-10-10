# GyroLock V16 — Stabilization Repair + Flash

Android camera project with gyro XYZ post-recording stabilization.

## Changes in V16
- Removed encoder-specific `-preset` usage from the stabilization command. The output command explicitly uses the broadly supported MPEG-4 encoder (`mpeg4`) and 30 FPS constant-frame-rate output.
- Uses `-fps_mode cfr` instead of the older `-vsync cfr` flag.
- Shows actual FFmpeg log details when stabilization fails, making future failures diagnosable. The original recording remains preserved.
- Added a quick torch/flash ON/OFF button at the top of the camera screen. This is continuous LED torch lighting, not a one-shot photo flash; it is disabled if the rear camera has no flash unit.
- Keeps FHD preference with HD/SD fallback, tap-to-focus, 1×/2×/4× zoom, gyro XYZ stabilization, mirror edge fill, and 30 FPS stabilized output.

## Important
The app records the original clip first, then creates a stabilized copy after recording stops. Gyro-only stabilization cannot perfectly remove all walking translation, parallax, rolling-shutter distortion, or motion blur. The preview transform is not encoded into the raw recording.

## Build with GitHub Actions
1. Upload the contents of this ZIP to the root of a GitHub repository.
2. Open Actions and run **Build GyroLock APK**.
3. Download `GyroLock-debug-apk` after the workflow succeeds.

## Validation status
The ZIP and source edits are checked locally, but this environment has not built the APK or tested it on a physical phone. Please test a short clip before relying on it. If stabilization still fails, V16 now exposes FFmpeg's log details in the app status so the exact cause can be corrected instead of guessed.
