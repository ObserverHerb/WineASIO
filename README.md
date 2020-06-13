# Purpose
WineASIO functions as a bridge between the [JACK Audio Connection Kit](https://jackaudio.org/) and any Windows audio software that relies on the
ASIO sound card driver protocol, [developerd by Steinberg](https://www.steinberg.net/en/company/developers.html), when running through [WINE](https://www.winehq.org/) on Linux.
### CMake Fork
As a hobbyist musician and producer, as well as Linux enthusiast, frustrated with the current Wild West state of WineASIO
maintenance and lack of a decent, modern build system, I set out to update the library to work with current versions of Wine as
well as wrap the project in the widely used [CMake](https://cmake.org/) meta build system to ease building the project both for individual users and
distribution package maintainers.

I'm am no expert with JACK or WINE, so contributions are welcome (frankly, soreley needed). Bug fixes in this fork are a
combination of my own efforts as well as cherry picks from various other forks on GitHub.

My primary objective is to keep
WineASIO in a functional state, so that consumers downstream can rely on it, without changing what already works too much. I'm
not opposed to adding completely new features but they're not my priority.

# Credits
I'm preserving these to the best of my ability to track them.
* Copyright (C) 2006 Robert Reif
* Portions copyright (C) 2007 Ralf Beck
* Portions copyright (C) 2007 Johnny Petrantoni
* Portions copyright (C) 2007 Stephane Letz
* Portions copyright (C) 2008 William Steidtmann
* Portions copyright (C) 2010 Peter L Jones
* Portions copyright (C) 2010 Torben Hohn
* Portions copyright (C) 2010 Nedko Arnaudov
* Portions copyright (C) 2011 Christian Schoenebeck
* Portions copyright (C) 2013 Joakim Hernberg
