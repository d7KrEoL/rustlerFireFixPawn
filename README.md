# rustlerFireFix Pawn filterscript
In mobile samp there is a bug. Rustler plane cannot damage players or vehicles if they're using mobile samp client. This script for samp server [Pawn] fixes it, so you can now damage all players and vehicles. 

## Dependencies
There is a different ways this script can work: it can transmit only damage to players, or it can transmit BulletSync data. So dependencies will be different for each method.
### Necessary dependencies:
- [rotations.inc by Shishka](https://github.com/Shiska/rotations)
- [ColAndreas plugin (Pottus)](https://github.com/Pottus/ColAndreas)
### Optional dependencies:
- [Pawn.RakNet plugin (katursis)](https://github.com/katursis/Pawn.RakNet) - if BulletSync is transmiting
- mobile.inc - if you want to distinguish Mobile client players from PC

## Compilation
1. Install all includes from dependencies list to your pawno
2. In rustlerFireFix.pwn you can fast-configure:
   - Uncomment `#include "mobile.inc"` on ≈10 line and from ≈170 to ≈174 lines (starting with `if (!IsPlayerMobile(targetid))`) if you want to distinguish Mobile client players from PC
   - `#define DEBUG_MODE [true/false]` - enable/disable printing debug messages in console and server log
   - `#define BULLET_SYNC_ENABLE [true/false]` - enable/disable BulletSync data packet to be transmitted to damaged player
   - `#define BULLET_SYNC_STREAM_ENABLE [true/false]` - enable/disable BulletSync data packet to be transmitted to all players in victim's stream area (only works if `BULLET_SYNC_ENABLE` is `true`)
3. Script now should be configured to your purposes and can be compiled

## Installation
1. Install all plugins from dependencies list to your server
2. Compile the script and place it into `filescripts` folder
3. Don't forget to place generated `ColAndreas.cadb` file into `scriptfiles/colandreas` folder. Script with pre-generated `ColAndreas.cadb` file can be found in any release archive.
4. Your server.cfg file should look something like this:
```C++
  bind 127.0.0.1
  echo RustlerFireFix server config file example
  lanmode 0
  rcon_password Rustler
  maxplayers 50
  port 7777
  hostname Rustler Fire Fix Demo Server
  gamemode0 lvdm 1
  filterscripts rustlerFireFix
  plugins ColAndreas pawnraknet
  announce 0
  chatlogging 0
  weburl sampmap.ru
  onfoot_rate 40
  incar_rate 40
  weapon_rate 40
  stream_distance 300.0
  stream_rate 1000
  maxnpc 0
  logtimeformat [%H:%M:%S]
  language English
```
