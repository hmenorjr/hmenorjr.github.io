---
title: "Fix Windows' WSL DNS Issue"
description: "My solution for the wsl2 DNS problem with ubuntu terminal and WindowsOS."
pubDate: "Jan 22 2024"
heroImage: "/unsplash-gabriel-heinzer.jpg"
---

# Beskar-Clad journey through Windows and WSL

## Introduction

In the vast galaxy of Windows Subsystem for Linux 2 (WSL2), Mandalorians seek the thrill of seamless integration between Windows and Linux. The promise of this union is enticing, but as any Mandalorian knows, the journey is seldom without challenges. One particularly notorious adversary arises when attempting to execute a simple `git clone` command, as DNS issues threaten to disrupt the peace. Fear not, here, we shall embark on an exhilarating quest to conquer these DNS foes and ensure your WSL2 endeavors remain epic.

## Forging Beskar for the Battle

Armed with the beskar-clad Windows environment and your trusty WSL2 armor, you stand ready to dive into coding conquests. As you execute the `git clone` command, a disturbance in the Force occurs—DNS-related errors rain down like blaster fire. Panic sets in, but remember, a Mandalorian never surrenders. We shall emerge victorious against these DNS demons!

## The Mysterious DNS Conundrum

The DNS challenge we face manifests as an inability to resolve domain names within the WSL2 environment. Error messages echo through the terminal:

```
fatal: unable to access 'https://github.com/username/repo.git/': Could not resolve host: github.com
```

The dark side is at play; WSL2 has its own DNS resolver, and it clashes with the Windows DNS settings.

## Unveiling the Solution: Forging an Alliance with the Force

### Step 1: Identifying the Dark Side

To unveil the source of this disturbance, inspect the DNS configuration within WSL2 using the command:

```bash
cat /etc/resolv.conf
```

Behold the IP address `172.28.0.1` (sample only of course), a dark presence causing the conflict.

### Step 2: Harnessing the Force

Fear not, brave Mando! We shall forge an alliance by configuring WSL2 to use a custom DNS resolver. Open your WSL2 configuration file (usually at `C:\Users\YourUsername\.wslconfig`) and add the following lines:

```plaintext
[wsl2]
dns=8.8.8.8
```

Replace `8.8.8.8` with the DNS server of your choosing.

### Step 3: Witness the Beskar Magic

Restart your WSL2 environment and witness the beskar magic unfold! Execute the `git clone` command once more, and watch as it effortlessly fetches the repository, akin to a Mandalorian reclaiming lost treasure.

## Conclusion: Conquer and Code On!

With the DNS demons defeated, you are free to unleash the Force within the WSL2 realm. The thrill of overcoming technical challenges is the essence of every Mandalorian's journey. May your code be as precise as a sniper's shot and your commits swift as a jetpack escape.

![Mandalorian Victory](path/to/mandalorian_victory.gif)

Happy coding, fearless Mandalorian!