# prewin10-ssh
SSH Client for Windows previous 10

download "installer_source" of:
http://www.mls-software.com/opensshd.html
download the newest .tar.xz:
ftp://ftp-stud.hs-esslingen.de/pub/Mirrors/sources.redhat.com/cygwin/x86_64/release/openssh/

or use the "cygwin_source*.zip" of the previous mls-software link

create a batch file with the following content:
```
if not exist %WinDir%\System32\OpenSSH mkdir %WinDir%\System32\OpenSSH
xcopy openssh\bin64\* %WinDir%\System32\OpenSSH\ /i /d /y /he /C
for /f %%i in ('dir /s /b /o:n /a:d ^| findstr openssh-* ^| findstr \usr\bin') do xcopy %%i\* %WinDir%\System32\OpenSSH\ /i /d /y /he /C
```

It will create a folder "OpenSSH" in example "C:\Windows\System32"
copy the content of the cygwin "installer_source" to it and search for the openssh-"version" folder and also copy the content to it.

Use the system preferences (win+pause) > advanced settings > system variables and edit the system env "Path"
we will add `;C:\Windows\System32\OpenSSH` at the end of the line.

open a new command prompt (win+r) "cmd" and enter for example ssh root@example.com.


this method isn't that good as the win10 version is but it is working! :p
