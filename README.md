# putty
Source code from putty [official](http://www.chiark.greenend.org.uk/~sgtatham/putty/) and add self customization.


# Build on Windows #
* [mingw-w64 v4.9.2](http://www.cr173.com/soft/132367.html)
* Below source files are updated to adapt to mingw env (already in current repo)
  - align type definition between `sshbn.h` and `_mingw.h`
    + `typedef __uint64_t BignumInt;` -> `typedef unsigned __int64 BignumInt;`
    + `typedef __uint128_t BignumDblInt;` -> `typedef unsigned __int128 BignumDblInt;`
  - update putty.rc, pageant.rc, puttygen.rc, puttytel.rc
    - Solve 64bit version issue: Not involve 32bit manifest `putty.mft` in 64bit build
    - REF: https://github.com/FauxFaux/PuTTYTray/issues/89
* a new makefile Makefile.mingw (already in current repo)
* In mingw
  - cd putty-src/windows
  - run `make -f Makefile.mingw`
* NOTE: for building by cygwin, please also follow above steps, except
  - aligin type definition in cygwin
  - remove option `-mno-cygwin` in Makefile.cyg. It is invalid in latest cygwin
  - run `make -f Makefile.cyg`

# Customization #
  - Add Keyboard hotkeys (session panel -> windown -> behavior)
    + F1: one key clean screen
    + F2: one key copy all
    + F3: duplicate session
    + F4: change current window title
  - Add SSH auto login with user name and password
  - Add find text

# Other Useful Tips #
* For login local cygwin
  * [puttycyg](https://code.google.com/archive/p/puttycyg/)
    - Project is dead, no longer maintained. The existing code only support cygwin1.5 and cygwin1.7. Now cygwin is going forward...
    - Great project. I even merged its source code to my putty. It can be replaced by cygtermd as describe in below bullet.
  * http://www.chiark.greenend.org.uk/~sgtatham/putty/wishlist/cygwin-terminal-window.html

# Contributor #
* Brian Jiang
* Alan ZHU
