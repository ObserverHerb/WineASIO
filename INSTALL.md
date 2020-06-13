The [Steinberg SDK](https://www.steinberg.net/en/company/developers.html) is required to build WineASIO. Due to its license, it is not possible to redistribute it here. CMake will download the Steinberg SDK for you, so an Internet connection is required to build this fork. You will also need the [JACK Audio Connection Kit](https://jackaudio.org/) and [libuuid](http://libuuid.sourceforge.net/) installed, as well as [pkg-config](https://www.freedesktop.org/wiki/Software/pkg-config/) for detecting their locations. Naturally, you will need to have [Wine](https://www.winehq.org/) installed prior to building WineASIO.

### CMake Options

#### `-DWINE_INSTALL_PREFIX=/usr`

Set this to the location of your system's Wine installation if it differs from the default.

#### `-DWIN64=OFF`
This defaults to OFF, meaning WineASIO will be built for a 32-bit [wineprefix](https://wiki.winehq.org/FAQ#Wineprefixes). If your wineprefix will be 64-bit, turn this ON.

#### `-DWINE_FLAVOR=wine`
This flag is highly dependent on your Linux distribution. For instance, [Gentoo Linux](https://www.gentoo.org/) can have multiple Wine installations installed at one time. The "flavor" determines which subdirectory the library gets installed into under the target installation path.

For example, if `-DWINE_INSTALL_PREFIX` is default (`/usr`), `-DWIN64` is `OFF`, and `-DWINE_FLAVOR` is set to `wine-staging-5.9`, then the library `.dll` file will ultimately be installed into `/usr/lib/wine-staging-5.9/wine`.

### CMake Example

Create a build directory under your source directory and `cd` into it. Then run CMake using a combination of the above options. For example, the following builds WineASIO for a 64-bit wineprefix on Gentoo.

```
cmake -DWIN64=ON -DWINE_FLAVOR=wine-staging-5.9 ..
```

After it's configured with CMake, you can build and install it.

```
make
make install
```

Note that `make install` may require you to use `sudo` or be `root` before running it.

### Registering With Wine

Before you can use WineASIO, you will need to register it in your wineprefix. On 32-bit wineprefixes, this can be done with the following.

```
regsvr32 wineasio.dll
```

If your wineprefix is 64-bit, use this instead.

```
wine64 regsvr32 wineasio.dll
```
