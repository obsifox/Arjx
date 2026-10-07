# Arjx

Arjx is a graphics renderer package for the mclauncher Android launcher. It appears in the mclauncher renderer list with the `alpha` tag.

## Package format

mclauncher downloads an Arjx release asset (`.tar.gz`, `.tar.xz`, `.tgz` or `.zip`) and extracts it to `.mclauncher/renderers/arjx/`. The directory must contain at least one shared object (`.so`). The launcher picks the renderer library in this order:

1. a library named in `libName` for the renderer entry
2. `libGL.so`
3. the first `lib*.so` in the directory

## Publishing a build

Attach the archive to a GitHub release in this repository. mclauncher resolves the asset dynamically through the GitHub releases API, so no launcher update is needed for new Arjx builds. A direct URL can also be set in the launcher settings (`Arjx url`).

## Integration notes

mclauncher injects the renderer through `-Dorg.lwjgl.opengl.libname=<absolute path to the .so>` and prepends the renderer directory to `LD_LIBRARY_PATH` before the game process starts. The library is expected to provide an OpenGL implementation over GLES on Android, compatible with the LWJGL OpenGL module.

## Status

alpha. Interfaces may change between builds while the renderer matures.
