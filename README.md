# Solaar rules for the MX Master 3S

Use the Logitech MX Master 3S thumb gestures, side buttons, and horizontal wheel with [Solaar](https://pwr-solaar.github.io/Solaar/) on Linux. These rules were tested with Solaar 1.1.20 on Arch Linux using a Logi Bolt receiver shared with an MX Keys S.

| Mouse input | Shortcut sent |
| --- | --- |
| Hold thumb button, swipe up, release | Super + W |
| Hold thumb button, swipe down, release | Super + D |
| Hold thumb button, swipe left, release | Super + Ctrl + Right |
| Hold thumb button, swipe right, release | Super + Ctrl + Left |
| Tap thumb button | Super |
| Back button | Dedicated Copy key |
| Forward button | Dedicated Paste key |
| Thumb wheel | Super + Equal or Super + Minus, depending on direction |

Your desktop and applications decide what these shortcuts do. To customize them, edit the `KeyPress` entries in Solaar’s Rule Editor. If the horizontal wheel feels reversed, swap `equal` and `minus` in the two wheel rules.

## Setup

1. If you use LogiOps, stop its service before letting Solaar take over the mouse. On a systemd system, run `sudo systemctl stop logid.service`. You can re-enable LogiOps later if needed.
2. Quit Solaar from its tray menu. Back up your existing `~/.config/solaar/rules.yaml` if you have one. Copy this repository’s `rules.yaml` to that path, or append its YAML documents to your existing rules file.
3. Start Solaar and select **MX Master 3S**. Set these device options:

   | Solaar setting | Value |
   | --- | --- |
   | Key/Button Diversion → Mouse Gesture Button | Mouse Gestures |
   | Key/Button Diversion → Back Button | Diverted |
   | Key/Button Diversion → Forward Button | Diverted |
   | Key/Button Diversion → Smart Shift | Regular |
   | Thumb Wheel Diversion | On |
   | Thumb Wheel Direction | Default (inversion off) |

   If a setting is marked **Ignore this setting**, click the icon beside it until you can edit it. Keeping the Smart Shift button on **Regular** lets the mouse handle its built-in wheel mode toggle.
4. Test the shortcuts with Solaar running. On Wayland, Solaar needs write access to `/dev/uinput` to send shortcut keys. See the [Solaar rule documentation](https://pwr-solaar.github.io/Solaar/rules/) if bindings register but shortcuts do not fire.
5. Once the bindings work, configure Solaar to start at login and disable the LogiOps service if it was enabled.

To roll back, quit Solaar, restore your previous rules, and set the changed diversion options back to their previous values before restarting your old gesture tool.
