# ld

rpath (now runpath) is used by *ld* to find dependencies.

remember that the library doing the actual ldopen call is the one who needs the
rpath, so if ldopen is in B and C calls B.loadSomething to get D, then B is the
one who needs the rpath.

cheatsheet:
- set rpath when compiling/linking: `-Wl,-rpath,\$ORIGIN`
- add rpath after compiling: `patchelf --add-rpath <rpath> <binary>`
- check current rpath: `readelf -d <binary>`
- debug libs loaded: `LD_DEBUG=libs <binary>`
- debug libs loaded from explicit ldopen calls: `lsof -T -P -p <pid>`
