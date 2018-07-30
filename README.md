# WinDynamicDesktop
Port of macOS Mojave Dynamic Desktop feature to Windows 10, available for download on GitHub and the Microsoft Store

[![GitHub releases](https://img.shields.io/github/downloads/t1m0thyj/WinDynamicDesktop/total.svg)](https://github.com/t1m0thyj/WinDynamicDesktop/releases)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/t1m0thyj/WinDynamicDesktop)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=H8ZZXM9ABRJFU)

<a href='//www.microsoft.com/store/apps/9NM8N7DQ3Z5F?ocid=badge'><img src='https://assets.windowsphone.com/85864462-9c82-451e-9355-a3d5f874397a/English_get-it-from-MS_InvariantCulture_Default.png' alt='Microsoft Store' width='160'/></a>

## Getting Started

The first time you run WinDynamicDesktop, it will automatically download the macOS Mojave wallpapers from [here](https://files.rb.gd/mojave_dynamic.zip) and extract them to your disk. I have not included the files directly in this repository for copyright reasons. If you want to select a different set of images, see the section below for how to do so.

You will also need to input your location when running the program for the first time. This location is not used for any purpose other than to determine the times of sunrise and sunset where you live.

After you enter your location, the program will minimize to your system tray and it will run in the background. Right-clicking on the system tray icon opens a menu with options to update the location, refresh the wallpaper manually if necessary, or exit the program. You can also choose to start WinDynamicDesktop when Windows boots or enable dark mode from this menu.

## Frequently Asked Questions

### Why did you develop this?

When the Dynamic Desktop feature was announced for macOS Mojave which shifts through 16 images of the same desert scene taken at different times of day, I wanted to write a Windows program that would do the same thing. Windows has the ability built-in to cycle through different wallpapers, but only at regular intervals, not based on the times of sunrise and sunset. This program adds that feature for the Mojave wallpapers to the Windows desktop.

### Can the lockscreen image be changed too?

This is a commonly requested feature, and it would be nice to mimic the behavior of macOS and many Linux distros where the lockscreen image is the same as the desktop wallpaper. This functionality would likely only be possible in the Microsoft Store version of the app, since there isn't a good API for changing the Windows lockscreen image in a .NET app. Currently I have decided not to implement this feature, because I would like to keep functionality consistent between both versions.

### How can I hide the tray icon?

If you want to run the app silently with no icon in the system tray, you can do this by editing the `settings.conf` file which is in the same folder as the EXE. Change the setting `"hideTrayIcon":false` to `"hideTrayIcon":true` (or add it if it doesn't exist), then restart the app.

### How can I customize the images?

By default WinDynamicDesktop uses the Mojave wallpapers, but if you create an `images.conf` file in the same folder as the EXE you can customize the images that are used. The default `images.conf` can be found [here](src/images.conf). It is formatted in JSON and must contain the following values:

* `themeName` - String which is the name of the wallpaper theme (e.g., "Mojave Default")
* `imagesZipUri` - String containing URL to download images.zip file from, or *null* if the content in the images subfolder is provided by the user
* `imageFilename` - String containing the filename of each wallpaper image, with `{0}` substituted for the image number
* `dayImageList` - Array of numbers listing the image numbers to display throughout the day (between sunrise and sunset)
* `nightImageList` - Array of numbers listing the image numbers to display throughout the night (between sunset and sunrise)

## Legal and Privacy Stuff
I do not own the Mojave wallpaper pictures used by WinDynamicDesktop, they belong to Apple. The icon used in this program was made by [Roundicons](https://www.flaticon.com/authors/roundicons) from [flaticon.com](https://www.flaticon.com/) and is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/).

When you enter your location, WinDynamicDesktop uses the [LocationIQ service](https://locationiq.org/) to convert your location to latitude and longitude. Your location info is never sent anywhere without your consent.
