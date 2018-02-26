# webN64

Copyright (C) 2018 Juergen Wothke

This is a JavaScript/WebAudio plugin of kode54's "LazyUsf2 - USF Decoder" (based on Mupen64plus). This 
plugin is designed to work with my generic WebAudio ScriptProcessor music player (see separate project). 

It allows to play "(Ultra) Nintendo 64 Sound" music (.USF/.MINIUSF2 files).

A live demo of this program can be found here: http://www.wothke.ch/webn64/


## Credits
The project is based on: https://gitlab.kode54.net/kode54/lazyusf2 


## Project
It includes most of the original "USF Decoder" code including all the necessary 3rd party dependencies. All the "Web" specific 
additions (i.e. the whole point of this project) are contained in the "emscripten" subfolder. Due to the unavailability of SSE2 
and x86 assembly code support in EMSCRIPTEN the "cached interpreter" mode is used.) The main interface 
between the JavaScript/WebAudio world and the original C code is the adapter.c file. Some patches were necessary 
within the original codebase (these can be located by looking for EMSCRIPTEN if-defs). 


## Howto build

You'll need Emscripten (http://kripken.github.io/emscripten-site/docs/getting_started/downloads.html). The make script 
is designed for use of emscripten version 1.37.29 (unless you want to create WebAssembly output, older versions might 
also still work).

The below instructions assume that the webn64 project folder has been moved into the main emscripten 
installation folder (maybe not necessary) and that a command prompt has been opened within the 
project's "emscripten" sub-folder, and that the Emscripten environment vars have been previously 
set (run emsdk_env.bat).

The Web version is then built using the makeEmscripten.bat that can be found in this folder. The 
script will compile directly into the "emscripten/htdocs" example web folder, were it will create 
the backend_n64.js library. (To create a clean-build you have to delete any previously built libs in the 
'built' sub-folder!) The content of the "htdocs" can be tested by first copying it into some 
document folder of a web server. 


## Depencencies

The current version requires version 1.02 (older versions will not
support WebAssembly) of my https://github.com/wothke/webaudio-player.

This project comes without any music files, so you'll also have to get your own and place them
in the htdocs/music folder (you can configure them in the 'songs' list in index.html).


## Disclaimer

This emulator is not as stable as I would like and there are songs which actually manage to crash 
it. From what I've read there does not seem to be one perfect Nintendo64 emulator and what works with 
one may fail with the next (and vice versa). And who knows, maybe future improvements will make this 
one more stable.


## License

This library is free software; you can redistribute it and/or modify it
under the terms of the GNU Lesser General Public License as published by
the Free Software Foundation; either version 2.1 of the License, or (at
your option) any later version. This library is distributed in the hope
that it will be useful, but WITHOUT ANY WARRANTY; without even the implied
warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301 USA
