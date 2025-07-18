# TunerHammer

Your own musical service.

TunerHammer is a project aiming to provide you a way to host your own musical infrastructure.

The idea is that you host your music files on your PC, then you're able to play music from all of your devices through a central Web server.

This lets you manage the playback across all your devices, just like Spotify.

## Idea Only

> [!IMPORTANT]
> Today, this project is only an idea. No actual app or server exists now.

## Platforms

TunerHammer will support these platforms:

- **Web**
  * Online player accessible anywhere
- **Windows**
  * Native player for Windows PCs
  * TunerHammer File Server
- **macOS**
  * Native player for Macs
  * TunerHammer File Server
- **Linux**
  * Native player following GNOME design guidelines
  * Native player following KDE design guidelines
  * TunerHammer File Server (CLI version)
  * TunerHammer Web App Server
  * TunerHammer API
- **Android**
  * Native player for Android phones and tablets
- **iOS**
  * Native player for iPhones and iPads
- **Android TV**
  * Native player for Android TV boxes

More platforms might be added later. Implementing TunerHammer player on any platform must be easy: you just call TunerHammer Client Core functions from the bare music player interface.

## Parts

TunerHammer will consist of multiple parts:

### TunerHammer Player

This is a native app you install on your device such as phone or PC.

It connects to the TunerHammer server and lets you either download all the music present there or stream it without having to take up space on your end device.

Then it lets you play the music, letting you manage the library: create your playlists, load new music into the library (you provide the music file yourself or download from YouTube from within the app) and etc.

It also syncs the playing status across all the devices connected to the same server. It might sound familiar if you use Spotify: if you're listening to a track on your phone and opening the app on your PC, you'll be able to control the playback on your phone from the PC.

Every native player builds upon TunerHammer Client Core. It's a shared library in C++ that does all the communication with the TunerHammer server.

### TunerHammer API

This is the central TunerHammer server. All players, the Web App Server and all File Servers must connect to it.

It doesn't actually serve any music files itself: it just centralizes all the communications in one place.

### TunerHammer File Server

This is a program that you run on your PC (or NAS) which must be connected to the TunerHammer API.

Once connected to the API, it hosts a folder to be accessible from the API.

For example, a File Server is running on your computer which has a folder with all your music. The File Server program connects to the API. TunerHammer Player also connects to the API and is now able to play music from your computer.

### TunerHammer Web App Server

This is a server that runs the Web version of the TunerHammer Player. It also must be connected to the TunerHammer API.

Once connected to the API, it serves a Web App accessible via any browser and which has all the functions of a native TunerHammer Player.
