# VEEW — Android Video Editor Project

- **Repository / Gradle root:** `VEEW`
- **Android app label:** `EVeditor`
- **Application ID / namespace:** `com.evc.app` (preserved to retain the existing app identity)
- **Version:** `0.2.181` (`versionCode 379`)
- **Minimum Android:** API 24
- **Target / Compile SDK:** 35
- **Target ABI:** `armeabi-v7a` (32-bit ARM)

## GitHub Actions and MGit

The workflow is `.github/workflows/android.yml`. It follows the previous FVW workflow pattern:

- Runs on pushes to every branch (`branches: ["**"]`).
- Supports pull requests and manual runs (`workflow_dispatch`).
- Uses JDK 17, Android SDK 35 / Build Tools 35.0.0, and Gradle 8.9.
- Builds the debug APK and uploads it as `VEEW-0.2.181-ARM32-Dynamic-Storyboard-debug-apk`.

This ZIP is prepared as a **fresh repository**: the old `.git` directory and old GitHub remote have been removed. Open the extracted `VEEW` folder as the local repository in MGit, initialize it, stage all files (including hidden `.github`), and create the first commit. Then create an empty GitHub repository named exactly `VEEW`, add that repository as the remote in MGit, and push the branch.

Keep the workflow file at exactly `.github/workflows/android.yml`; do not place the project inside an extra nested folder. The workflow intentionally watches all branches so a push to a branch other than `main` or `master` still starts Actions.

## Latest carried-over changes from FVW 0.2.178

- All View shows only the storyboard command row and storyboard table.
- Auto Crop and Cut are removed from the player-side column; the main player row is top-aligned.
- Tracks, overlay video, and text controls are grouped together.
- Storyboard spacing label and input were enlarged threefold.
- Storyboard frame extraction uses two independent workers / metadata retrievers.
- Timeline thumbnail extraction starts after storyboard extraction to reduce contention.
- Timeline sample thumbnails were reduced from 48 to 24.
- Selecting a new video clears custom spacing without triggering an unintended duplicate storyboard reload; pending callbacks are cancelled.

## Build and verification status

The source and XML are carried forward from FVW 0.2.178. The workflow configuration has been updated for the new repository identity and corrected artifact version. An Android build and on-device performance test have **not** been confirmed in this package-preparation environment. Verify the first GitHub Actions run and test storyboard rendering on the target ARM32 device.
