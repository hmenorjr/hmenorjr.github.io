---
title: "Upgrading Python2 to Python3 on a MacOS using Homebrew"
description: "A gist on how I solved upgrading my Python using homebrew instead of the manual installation."
pubDate: "Jun 5 2020"
heroImage: "/unsplash_james_harrison.jpeg"
---

## Foreword
Like most developers using MacOS or OSX, we use `Homebrew`` to install and update software/casks. As of this writing, I was having challenges updating Python2 to Python3.

## What I Did
### Check Version
After executing the this command: `$ brew info python`

The result:
```
python: stable 3.7.7 (bottled), HEAD
Interpreted, interactive, object-oriented programming language
https://www.python.org/
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/python.rb
==> Dependencies
Build: pkg-config ✘
Required: gdbm ✔, openssl@1.1 ✔, readline ✔, sqlite ✔, xz ✔
==> Options
--HEAD
    Install HEAD version
==> Caveats
Python has been installed as
  /usr/local/bin/python3
Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to`python3`, `python3-config`, `pip3` etc., respectively, have been installed into 
  /usr/local/opt/python/libexec/bin
You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /usr/local/lib/python3.7/site-packages
See: https://docs.brew.sh/Homebrew-and-Python
==> Analytics
install: 198,504 (30 days), 1,021,773 (90 days), 5,245,160 (365 days)
install-on-request: 162,871 (30 days), 639,716 (90 days), 2,755,324 (365 days)
build-error: 0 (30 days)
```

### Installing with Homebrew
Now the fun begins. I ran `brew install python` and got some errors.
```
Error: The `brew link` step did not complete successfully
The formula built, but is not symlinked into /usr/local
Could not symlink bin/2to3
Target /usr/local/bin/2to3
already exists. You may want to remove it:
  rm '/usr/local/bin/2to3'
To force the link and overwrite all conflicting files:
  brew link --overwrite python
To list all files that would be deleted:
  brew link --overwrite --dry-run python
Possible conflicting files are:
/usr/local/bin/2to3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/2to3
/usr/local/bin/idle3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/idle3
/usr/local/bin/pydoc3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/pydoc3
/usr/local/bin/python3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/python3
/usr/local/bin/python3-config -> /Library/Frameworks/Python.framework/Versions/3.8/bin/python3-config
Error: Permission denied @ dir_s_mkdir - /usr/local/Frameworks
```

I tried removing the folder one by one and forgot you can just override it. Don't worry, it's safe. (^^,)
This is done by running: `$ brew link --overwrite python`

> DJ Khaled!!!

![DJ Khaled Another One](/another_one_dj_khaled.jpeg "DJ Khaled Another One")

Here's the error:
```Linking /usr/local/Cellular/python/3.7.7... Error: Permission Denied @ dir_s_mkdir — /usr/local/Frameworks```

#### Google is our Friend
Privacy not included

Turns out it's an existing issue. Remember, Homebrew doesn't allow or recommend to execute brew commands with sudo anymore to prevent issues. Source: https://github.com/Homebrew/homebrew-core/issues/30652

So we execute the following commands:
```
$ sudo mkdir /usr/local/Frameworks
$ sudo chown $USER /usr/local/Frameworks
```

Then, we execute `$ brew link python`

### Final Result
`$ Linking /usr/local/Cellular/python/3.7.7... 5 symlinks created`

## Get Involved
I'm not a fan of paywall. However, if this helped you, consider donating for coffee... or pizza.
https://ko-fi.com/hmenojr