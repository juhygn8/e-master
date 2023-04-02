= Overview =

This directory needs to contain the external libraries used by e.

= Installation =

The easiest way to do this is to run the included shell script
(needs cygwin installed). It will download, patch and add msvc
specific project files. Just open a cygwin shell, cd to this
directory and run:

  ./get_externals_win.sh

The libraries can be manually downloaded from the following sites:

  libcurl-7.18.2
  http://curl.haxx.se/download.html

  libtomcrypt-1.11
  http://libtom.org/?page=download&newsitems=5&whatfile=crypt
  Alternate URL: http://libtomcrypt.com/download.html

  libtommath-0.39
  http://libtom.org/?page=download&newsitems=5&whatfile=ltm
  
  metakit
  http://www.equi4.com/metakit/overview.html
  
  pcre-7.6
  http://pcre.org/
  
  tinyxml
  http://sourceforge.net/projects/tinyxml
  
They all need to be built as static libraries.

There are project files for Visual C++ in the subdir "build_msvc".
If you choose to use these, they will have to be copied into the source
directories of the individual projects.

A few libaries need to be patched to be used in e. The patches can be
found in the "patches" subdirectory.

When building the libraries you need to build the following solution files 
(make sure to select Debug or Release configuration):

curl\lib\curllib.sln (curllib)
libtomcrypt\libtomcrypt.sln (libtomcrypt)
libtommath\libtommath.sln (libtommath)
metakit\win\msvc90\mksrc.sln (mklib)
pcre\pcre.sln (pcre)
tinyxml\tinyxml.sln (tinyxml)

= OS notes =

On 64-bit versions of Windows, the folders created by cygwin can have 
incorrect permissions. `get_externals_win.sh` may also be run from a
msysgit bash prompt, but you need to first manually install the `mktemp`
utility into git's bin folder.

mktemp:
http://downloads.sourceforge.net/mingw/mktemp-1.5-MSYS.tar.bz2
