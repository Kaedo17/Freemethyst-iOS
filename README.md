# Freemethyst (iOS)
[![Development build](https://github.com/Kaedo17/Freemethyst-iOS/actions/workflows/development.yml/badge.svg?branch=main)](https://github.com/Kaedo17/Freemethyst-iOS/actions/workflows/development.yml)

Freemethyst is a fork of [Amethyst](https://github.com/AngelAuraMC/Amethyst-iOS), a Minecraft: Java Edition launcher for iOS and iPadOS, based off of zhuowei's [Boardwalk](https://github.com/zhuowei/Boardwalk) project. This fork removes the offline/demo account restriction and adds Java 25 support for Minecraft 26.x.

## What's different from Amethyst

- **No offline/demo account restriction** — all accounts can play the full game without demo mode limits
- **Java 25 support** — run the latest Minecraft 26.x versions that require Java 25
- **CI runs on free GitHub Actions runners** — no MacStadium dependency
- **Updated CI with modern Node.js** — `set-output` replaced with `$GITHUB_OUTPUT`, actions updated

## Features

- Supports most versions of Minecraft: Java Edition, from the very first beta to the newest snapshots.
- Supports Forge, Fabric, OptiFine, and Quilt for you to customize the experience with supported mods.
- Includes customizable on-screen controls, keyboard and mouse support, and game controller support.
- Optimized for jailbroken and TrollStore devices to enable better capabilities.
- Microsoft account and local account support for logging into Minecraft.
- ...and much more!

This repository contains the code for our iOS and iPadOS port. Looking for [Android?](https://github.com/AngelAuraMC/Amethyst-Android)

## Getting started with Freemethyst

The [Amethyst wiki](https://wiki.angelauramc.dev/wiki/getting_started/INSTALL.html#ios) has extensive documentation on how to install, set up, and play! For those who wish to install quickly, here's the basics:

### Requirements
At the minimum, you'll need one of the following devices on **iOS 14.0** and later:
- iPhone 6s and later
- iPad (5th generation) and later
- iPad Air (2nd generation) and later
- iPad mini (4th generation) and later
- iPad Pro (all models)
- iPod touch (7th generation)

However, we recommend one of the following devices on **iOS 14.0** and later:
- iPhone XS and later, excluding iPhone XR and iPhone SE (2nd generation)
- iPad (10th generation) and later
- iPad Air (4th generation) and later
- iPad mini (6th generation) and later
- iPad Pro (all models, except for 9.7-inch)

Recommended devices provide a smoother and more enjoyable gameplay experience compared to other supported devices.
- iOS 17.x and iOS 18.x is supported. However, a computer is required. For more information, please check out [the official wiki](https://wiki.angelauramc.dev/wiki/faq/ios/JIT.html#what-are-the-methods-to-enable-jit)

### Setting up to sideload
Freemethyst can be sideloaded in many ways. Our recommended solution is to install [TrollStore](https://github.com/opa334/TrollStore) if your iOS version supports it. Installing with TrollStore allows you to permanently sign the application, automatically enable JIT, and increase memory limits.

If you cannot, [AltStore](https://altstore.io) and [SideStore](https://sidestore.io) are your next best options.
- Signing services that do not use your UDID (and use distribution certificates) are not supported, as Freemethyst requires capabilities they do not allow. However, if you do managed to gain access to a Development certificate, due to it having the necessary entitlement (being com.apple.security.get-task-allow) to attach a debugger to the running process (enabling JIT), you may use a Development certificate.
  
- Only install sideloading software and Freemethyst from trusted sources. We are not responsible for any harm caused by using unofficial software.
- Jailbreaks also benefit from permenant signing, autoJIT, and increased memory limits. However, we do not recommend them on devices intended for regular use.

### Installing Freemethyst
#### Build from source
1. Clone the repository and its submodules.
2. Run `gmake dsym package PLATFORM=2` to build for iOS.
3. Find the IPA in the `artifacts/` directory.

#### Nightly builds
*These builds can contain game-breaking bugs. Use with caution.*
1. Download an IPA build of Freemethyst in the [Actions tab](https://github.com/Kaedo17/Freemethyst-iOS/actions).
2. Open the downloaded IPA in your sideloading app to install.

### Enabling JIT
Freemethyst makes use of **just-in-time compilation**, or JIT, to provide usable speeds for the end user. JIT is not supported on iOS without the application being debugged, so workarounds are required to enable it. You can use this chart to determine the best solution for you and your setup.
| Application         | AltStore | SideStore | StikDebug | TrollStore | Jitterbug          | Jailbroken |
|---------------------|----------|-----------|-----------|------------|--------------------|------------|
| Requires ext-device | Yes      | Yes (#)   | Yes (#)   | No         | If VPN unavailable | No         |
| Requires Wi-Fi      | Yes      | Yes (#)   | Yes (#)   | No         | Yes                | No         |
| Auto enabled        | Yes (*)  | No        | Yes       | Yes        | No                 | Yes        |

(*) AltServer running on the local network is required.
(#) Only the first time.

## Java runtimes
Freemethyst bundles the following Java runtimes for iOS aarch64:
- **Java 8** for older Minecraft versions
- **Java 17** for Minecraft 1.18–1.20
- **Java 21** for Minecraft 1.21
- **Java 25** for Minecraft 26.x (downloaded from [vibecodest/Amethyst-iOS](https://github.com/vibecodest/Amethyst-iOS) releases)

## Contributors
Freemethyst is a fork of Amethyst by @crystall1nedev and the Amethyst team. JRE 25 support is based on work from [catsruledogs/Amethyst-iOS-25](https://github.com/catsruledogs/Amethyst-iOS-25) and [vibecodest/Amethyst-iOS](https://github.com/vibecodest/Amethyst-iOS).

Notable names from the original Amethyst project:

@crystall1nedev - Project manager, iOS port developer  
@khanhduytran0 - iOS port developer  
@artdeell  
@Mathius-Boulay  
@zhuowei  
@jkcoxson   
@Diatrus 

## Third party components and their licenses
- [Caciocavallo](https://github.com/PojavLauncherTeam/caciocavallo): [GNU GPLv2 License](https://github.com/PojavLauncherTeam/caciocavallo/blob/master/LICENSE).
- [jsr305](https://code.google.com/p/jsr-305): [3-Clause BSD License](http://opensource.org/licenses/BSD-3-Clause).
- [Boardwalk](https://github.com/zhuowei/Boardwalk): [Apache 2.0 License](https://github.com/zhuowei/Boardwalk/blob/master/LICENSE) 
- [GL4ES](https://github.com/ptitSeb/gl4es) by @lunixbochs @ptitSeb: [MIT License](https://github.com/ptitSeb/gl4es/blob/master/LICENSE).
- [Mesa 3D Graphics Library](https://gitlab.freedesktop.org/mesa/mesa): [MIT License](https://docs.mesa3d.org/license.html).
- [MetalANGLE](https://github.com/khanhduytran0/metalangle) by @kakashidinho and ANGLE team: [BSD 2.0 License](https://github.com/kakashidinho/metalangle/blob/master/LICENSE).
- [MoltenVK](https://github.com/KhronosGroup/MoltenVK): [Apache 2.0 License](https://github.com/KhronosGroup/MoltenVK/blob/master/LICENSE).
- [openal-soft](https://github.com/kcat/openal-soft): [LGPLv2 License](https://github.com/kcat/openal-soft/blob/master/COPYING).
- [Azul Zulu JDK](https://www.azul.com/downloads/?package=jdk): [GNU GPLv2 License](https://openjdk.java.net/legal/gplv2+ce.html).
- [LWJGL3](https://github.com/PojavLauncherTeam/lwjgl3): [BSD-3 License](https://github.com/LWJGL/lwjgl3/blob/master/LICENSE.md).
- [LWJGLX](https://github.com/PojavLauncherTeam/lwjglx) (LWJGL2 API compatibility layer for LWJGL3): unknown license.
- [DBNumberedSlider](https://github.com/khanhduytran0/DBNumberedSlider): [Apache 2.0 License](https://github.com/immago/DBNumberedSlider/blob/master/LICENSE)
- [fishhook](https://github.com/khanhduytran0/fishhook): [BSD-3 License](https://github.com/facebook/fishhook/blob/main/LICENSE).
- [shaderc](https://github.com/khanhduytran0/shaderc) (used by Vulkan rendering mods): [Apache 2.0 License](https://github.com/google/shaderc/blob/main/LICENSE).
- [NRFileManager](https://github.com/mozilla-mobile/firefox-ios/tree/b2f89ac40835c5988a1a3eb642982544e00f0f90/ThirdParty/NRFileManager): [MPL-2.0 License](https://www.mozilla.org/en-US/MPL/2.0)
- [AltKit](https://github.com/rileytestut/AltKit)
- [UnzipKit](https://github.com/abbeycode/UnzipKit): [BSD-2 License](https://github.com/abbeycode/UnzipKit/blob/master/LICENSE).
- [DyldDeNeuralyzer](https://github.com/xpn/DyldDeNeuralyzer): bypasses Library Validation for loading external runtime
- Thanks to [MCHeads](https://mc-heads.net) for providing Minecraft avatars.
