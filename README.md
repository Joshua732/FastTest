# Build Colosseum's Windows AirsimWrapper.dll without installing Visual Studio

This GitHub Actions workflow uses GitHub's `windows-2022` runner and the Visual Studio 2022 MSVC toolchain to build the Colosseum Unity native plugin. It downloads Colosseum and a standalone Eigen 3.4.0 source archive (the historical Git submodule URL is unavailable), builds the native dependencies, fixes the Unity project file's outdated `rpclib` include path, and uploads the resulting `AirsimWrapper.dll` as a GitHub Actions artifact.

**Status:** The workflow has been reviewed against Colosseum's current `build.cmd`, `Unity/build.cmd`, and Unity wrapper project configuration, but it has **not been executed or verified by a successful Windows build**. If it fails, check the GitHub Actions logs.

## Steps

1. Sign in to https://github.com/new and create a new repository, for example `colosseum-unity-dll-builder`. Select **Add a README file** so it has a default branch.
2. In your new repository, click **Add file > Create new file**.
3. In the filename field, enter `.github/workflows/build-unity-dll.yml`.
4. Copy the entire contents of `.github/workflows/build-unity-dll.yml` from this package into the GitHub editor, and **Commit changes** to the default branch.
5. Open the repository **Actions** tab. Click **Build Colosseum AirsimWrapper DLL** in the left menu, then **Run workflow** and confirm.
6. If the build succeeds, open the completed run and download the **AirsimWrapper-Windows-x64** artifact ZIP.
7. Unzip the artifact and copy `AirsimWrapper.dll` to your Unity project under `UnityDemo/Assets/Plugins/` (replace with your own Unity project's `Assets/Plugins/` if needed).
8. Reopen Unity and test the `SimModeSelector` scene. Note that the runtime may require other dependency DLLs depending on the resulting build.

This is not a prebuilt DLL; the downloaded artifact will contain the DLL only after GitHub Actions compiles it successfully.

Source: https://github.com/CodexLabsLLC/Colosseum
