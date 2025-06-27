# mako

# This repository is being archived.  I am no longer maintaining or pulling changes from the official mako repository.

### This is mainly due to the fact that swaywm 1.11 seems to have an issue that causes mako and dunst to fail showing notifications after a monitor is powered off/on.  I have read that it is fixed in newer releases of sway that I can't build and install on my machine without causing compatibility issues with other desktops.  I am not willing to deal with some workarounds that do not work 100% of the time anyway so I am no longer using mako or dunst.


This fork adds the ability to create a new notification using the replace id instead of generating an new id for each notification.
---

A lightweight notification daemon for Wayland. Works on Sway.

<p align="center">
  <img src="https://github.com/user-attachments/assets/25582bd6-bd3b-4bb3-b248-87fa7f88e967" alt="mako screenshot">
</p>

mako implements the [FreeDesktop Notifications Specification][spec].

Feel free to join the IRC channel: #emersion on irc.libera.chat.

## Running


`mako` will run automatically when a notification is emitted. This happens via
D-Bus activation, so you don't really need to explicitly start it up (this also
allows delaying its startup time and speed up system startup).

If you have several notification daemons installed though, you might want to
explicitly start this one. Some ways of achieving this is:

- If you're using Sway you can start mako on launch by putting `exec mako` in
  your configuration file.

- If you are not using systemd, you might need to manually start a dbus user
  session: `dbus-daemon --session --address=unix:path=$XDG_RUNTIME_DIR/bus`

## Configuration

`mako` can be extensively configured and customized - feel free to read more
using the command `man 5 mako`

For control of mako during runtime, `makoctl` can be used; see `man makoctl`

## Building

Install dependencies:

* meson (build-time dependency)
* wayland
* pango
* cairo
* systemd, elogind or [basu] (for the sd-bus library)
* gdk-pixbuf (optional, for icons support)
* dbus (runtime dependency, user-session support is required)
* scdoc (optional, for man pages)

Then run:

```shell
meson build
ninja -C build
build/mako
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/4b32fef6-61d9-4ad1-8820-d4e5a245a76c" width="512" alt="mako">
</p>

## I have a question!

See the [faq section in the wiki](https://github.com/emersion/mako/wiki/Frequently-asked-questions).

## License

MIT

[spec]: https://specifications.freedesktop.org/notification-spec/latest/
[basu]: https://github.com/emersion/basu
