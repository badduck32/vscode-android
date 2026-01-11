# vscode-android
Repository to be able to run VSCode (or rather Code Server) on Android

# Features
- Minimal webview to run Code Server in
- Userscript support to add fixes to potential issues, as touchscreen devices aren't officially supported for VSCode (TODO: add GitHub issues source)
- Script that can be added to Termux to launch Code Server and the webview with 1 click from your homescreen (essentially acting like any other app on your device)

# Usage
There are 3 main parts to this repository:
- The VSCode launch script
- The userscript
- The webview

The explanations below will dive into how to use each part.

## VSCode launch script
This is a small Termux script. You can put this in the `.shortcuts` directory to create a shortcut on your home screen that launches VSCode and the webview at once. If you choose to use the Hermit app instead of the provided webview apk, then you will have to make some changes to this script, but this is described in the "Using Hermit instead".

I personally have set up an alias that runs this script whenever I write the command `code` in Termux, to make it more similar to VSCode on Linux.

## Userscript
This userscript provides some fixes to common issues with Code Server on Android. WIP

## Webview
This repository provides a webview in the releases tab, built using the [website-to-apk](https://github.com/Jipok/website-to-apk) project. This is all done manually, if someone can figure out how to do this in GitHub Actions and wants to create a PR, feel free to do so.

### Using Hermit instead
You can use a Hermit webview instead, and manually add the userscript to it. This is however not recommended, as userscripts in Hermit are a premium feature. Also, the VSCode launch script then also needs to be changed as follows: TODO

For now (mostly out of lazyness) Hermit is being used for this project.

# FAQ
### Why does this project need to exist if something like VHEditor already exists?
VHEditor is great, but the fact it doesn't use stock Termux and only it's own built in Termux creates issues. For example, the `am start` command simply doesn't work in VHEditor, so opening other apps from the VSCode terminal is impossible.

### Why don't we use VHEditor's webview instead?
A possibility would be to extract VHEditor's webview and build it as a standalone APK for this project. I am reluctant to do this though, as I've noticed performance issues with VHEditor's webview (and I've not looked at licensing constraints yet). If you really want to use VHEditor's webview, you still can, by only opening its webview and not running its Code Server. I have tried this in the past and it works decently well.
