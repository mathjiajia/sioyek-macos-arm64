# Sioyek development for Apple Silicon

Automatic macOS arm64 builds of [ahrm/sioyek's development branch](https://github.com/ahrm/sioyek/tree/development).

[Download builds](https://github.com/mathjiajia/sioyek-macos-arm64/releases) · [Build status](https://github.com/mathjiajia/sioyek-macos-arm64/actions/workflows/build.yml)

The workflow checks upstream every five minutes and builds the newest development commit when it has no complete release. GitHub may delay scheduled runs. Commits arriving between checks are combined into a build of the newest revision. Failed or incomplete builds are retried on the next check.

Builds run on GitHub's Apple Silicon `macos-15` runners with Qt 6.8.3 and require macOS 15 or newer. Each release has one download: **`sioyek-macos-arm64.dmg`**. Qt libraries and Sioyek's resources are bundled in the app.

Open the DMG and drag Sioyek to Applications. These development builds are ad-hoc signed and are not notarised. macOS may require approval in System Settings → Privacy & Security on first launch.

The DMG's `Source/` folder contains the complete corresponding Sioyek source archive with recursive submodules, the build workflow, and build provenance. The DMG's SHA-256 checksum is in the release notes.

To run a check manually, open **Actions → Sioyek development for Apple Silicon → Run workflow**. Select **force** to rebuild the current upstream commit. Changes to the build workflow also trigger a check.

Successful builds verify the executable and bundled libraries have arm64 support, check that libraries resolve inside the bundle or to macOS system libraries, verify the app signature and required resources, and run `sioyek --help` without the Qt installation's environment variables. This startup check does not certify PDF rendering or every GUI feature.

The workflow uses the repository's automatic `GITHUB_TOKEN`; no personal access token or Apple Developer certificate is required. A small heartbeat commit after 30 days without pushes keeps GitHub's public scheduled-workflow inactivity limit from stopping polling.

Sioyek and its dependencies retain their upstream licences. See the bundled licences and the complete source archive inside each DMG.
