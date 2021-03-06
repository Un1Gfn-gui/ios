<!--
https://mail.google.com/mail/u/0/#inbox
https://www.theiphonewiki.com/wiki//System/Library/CoreServices/SpringBoard.app
https://github.com/theos/theos/wiki/Upgrading-from-legacy-Theos
https://github.com/theos/theos/wiki/Structure
https://github.com/theiostream/theos-ref
https://github.com/theos/theos/wiki/Installation-Linux
https://github.com/theos/theos/issues/131
https://docs.godotengine.org/en/stable/development/compiling/cross-compiling_for_ios_on_linux.html
https://docs.huihoo.com/godotengine/godot-docs/godot/reference/cross-compiling_for_ios_on_linux.html
https://demensdeum.com/blog/2020/05/01/linux-to-ios-crosscompile-sdl/
https://docs.godotengine.org/en/latest/development/compiling/cross-compiling_for_ios_on_linux.html
https://github.com/theos/theos/wiki/NIC
https://github.com/theos/theos/wiki/Installation
-->

<!--
https://clang.llvm.org/docs/CrossCompilation.html
https://iphonedevwiki.net/index.php/Theos
https://github.com/theos/theos/wiki/Features
https://iphonedevwiki.net/index.php/Theos/Setup
https://github.com/theiostream/theos-ref/blob/master/theosref_legacy.md
-->

### [Theos](https://github.com/theos/theos)

<!-- https://github.github.com/gfm/#html-block -->
<details><summary>dependency graph</summary>

---

![TheosDepsGraph](./theos.svg)

---

</details>

[autoconf --build --host --target](https://www.gnu.org/software/autoconf/manual/autoconf-2.68/html_node/Specifying-Target-Triplets.html)

[sdks](https://github.com/theos/sdks) [nic](https://github.com/theos/nic) [logos](https://github.com/theos/logos)

```plain
THEOS=/opt/theos
```

<!-- https://github.github.com/gfm/#hard-line-breaks -->
[clang6.x?](https://github.com/theos/theos/wiki/Installation-Linux)\
[dpkg-deb LZMA?](https://github.com/theos/theos/wiki/Upgrading-from-legacy-Theos)

```plain
$ clang \
  -v \
  -target aarch64-apple-darwin \
  -L/opt/theos/sdks/iPhoneOS14.4.sdk/usr/lib \
  -F/opt/theos/sdks/iPhoneOS14.4.sdk/System/Library/Frameworks \
  -Wall \
  -Wextra \
  test.c
```

send w/ scp

```plain
$ ldid -S a.out
```

or

```plain
# sysctl -w security.mac.proc_enforce=0 security.mac.vnode_enforce=0
$ ./a.out
# sysctl -w security.mac.proc_enforce=1 security.mac.vnode_enforce=1
```

https://github.com/theos/theos/wiki/NIC

```bash
#
source ~/ios/ios.bashrc
$THEOS/bin/nic.pl -t iphone/tool -n toggleproxy -p com.Un1Gfn.toggleproxy -u "Darren Ng"
#
make
scp2 ./.theos/obj/debug/toggleproxy
#
make package
make install
ssh2 uicache
#
make uninstall
make clean; rm -rfv packages/ .theos/
ssh2 uicache
#
```

---

### Social

Stack Overflow
[#cydia](https://stackoverflow.com/questions/tagged/cydia)
[#jailbreak](https://stackoverflow.com/questions/tagged/jailbreak)
[#theos](https://stackoverflow.com/questions/tagged/theos)

[r/jailbreak](https://www.reddit.com/r/jailbreak)

---

### [iPhone Dev Wiki](https://iphonedevwiki.net/index.php/Main_Page)

[Getting_Started](http://iphonedevwiki.net/index.php/Getting_Started)

[Advice_for_new_developers](http://iphonedevwiki.net/index.php/Advice_for_new_developers)

[Theos](https://iphonedevwiki.net/index.php/Theos)

[CodeSigning](http://iphonedevwiki.net/index.php/Code_Signing) ([ldid](http://iphonedevwiki.net/index.php/Ldid))

---

### [The iPhone Wiki](https://www.theiphonewiki.com)

[SwitchBoard: /usr/local/bin](https://www.theiphonewiki.com/wiki/SwitchBoard:_/usr/local/bin)

[/System/Library/CoreServices/SpringBoard.app](https://www.theiphonewiki.com/wiki//System/Library/CoreServices/SpringBoard.app)

```plain
$ dpkg -S /usr/bin/uicache
uikittools: /usr/bin/uicache
```

[Cydia](https://www.theiphonewiki.com/wiki/Cydia.app)
([Errors](https://www.theiphonewiki.com/wiki/Cydia_Errors))
([CydiaSubstrate](https://www.theiphonewiki.com/wiki/Cydia_Substrate))

[syslog](https://www.theiphonewiki.com/wiki/System_Log)

[ECID](https://www.theiphonewiki.com/wiki/ECID)

<!-- https://github.github.com/gfm/#hard-line-breaks -->
**Always save [SHSH](https://www.theiphonewiki.com/wiki/SHSH) before upgrading**\
[Cydia_SHSH_Server](https://www.theiphonewiki.com/wiki/Cydia_SHSH_Server) ->
[Tss saver](https://tsssaver.1conan.com/v2/) ->
[1conan/com.1conan.tsssaver](https://repo.1conan.com/)

---

[D0m0/CocoaTop](https://github.com/D0m0/CocoaTop)

[iFixit](https://www.ifixit.com/)

[iOS CFW Guide](https://ios.cfw.guide/) -
[Recommended Repos](https://ios.cfw.guide/recommended-repos) -
[Cydia Packages Search](https://www.ios-repo-updates.com/) -
[Twickd Repo](https://repo.twickd.com/)

[MarimbaRemix](https://www.zedge.net/find/ringtones/marimba%20remix)

[Fandom Apple Wiki](https://apple.fandom.com/wiki/Main_Screen)

/etc/passwd passwd(5)

```
$ ssh mobile@192.168.1.17 cat /etc/passwd | grep -v -e'^#' -e'^_' | cut -d: -f1,3- | column -o: -s: -t
nobody:-2 :-2 :Unprivileged User   :/var/empty :/usr/bin/false
root  :0  :0  :System Administrator:/var/root  :/bin/sh
mobile:501:501:Mobile User         :/var/mobile:/bin/sh
daemon:1  :1  :System Services     :/var/root  :/usr/bin/false
```

https://stackoverflow.com/questions/45464584/macosx-which-dynamic-libraries-linked-by-binary

```
export DYLD_PRINT_LIBRARIES=1
export DYLD_PRINT_LIBRARIES_POST_LAUNCH=1
export DYLD_PRINT_RPATHS=1
```

https://stackoverflow.com/questions/15202441/ios-6-x-open-command-line-on-jailbreak

[AppSync](https://github.com/angelXwind/AppSync) + [appinst](https://github.com/angelXwind/AppSync/tree/master/appinst)

```bash
ipconfig getifaddr en0
```

https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html

/var/mobile/Containers/Data/Application

/var/containers/Bundle/Application

/Applications/MobileSafari.app

/private/var/mobile/Library/Mobile Documents/com\~apple\~CloudDocs/Downloads/

---
