# Tribal Hunter Archipelago Randomizer
An Archipelago integration for Tribal Hunter. Explore the island, send items to other players as you complete checks, and receive the abilities and upgrades you need to finish your own run. You can play solo or join a multiworld with other games.

This is the 0.1 public playtest, using AP world v0.8.0. The default settings include 539 checks. The room logic was reviewed by hand, and reports of missed requirements or inaccessible checks are welcome.

## What is randomized?
- Movement abilities, key items, size unlocks, and special powers
- Popshrooms, treasure chests, boss chests, and flight statue rewards
- Ability menu purchases, fox training rewards, and finite shop stock
- Kitora course completion rewards and artist encounters
The player YAML lets you choose which optional check pools to shuffle. You can also configure the starting statue, Ancient Path flight gates, upgrade prices, enemy rewards, traps, and DeathLink.

## Goals
Choose one or more goals when generating your seed.
- Defeat the true final boss.
- Defeat Lord Dread in the finale.
- Unlock 1,700 maximum fullness capacity.
If you select multiple goals, you can require all of them or let any one finish the run.

### Playing the randomizer
The mod supports Steam build 15863961 and GOG 1.0.2.4. Choose the patch for your edition and install it with TH Mod Manager or Delta Patcher.

# Tribal Hunter Archipelago setup
Use the patch for your Windows edition of Tribal Hunter, either **GOG 1.0.2.4** or **Steam build 15863961**. The package was tested with Archipelago **0.6.7**. The game name shown in Archipelago is **Tribal Hunter Base Development**.

## Install the mod

1. Close Tribal Hunter and make a separate copy of its game folder. Keep the original installation available for regular play.
2. Extract the mod archive for your edition. In Delta Patcher, select the clean `data.win` from that edition as the original file and select the matching xdelta patch from the table below. Enable **Backup original file** before applying the patch to the copy.
3. Put `gm-apclientpp.dll`, `ap-item.png`, and `ap-test.ini` next to `Tribal Hunter.exe` and the patched `data.win` in the copied game folder.
4. Launch `Tribal Hunter.exe` from that folder. On Linux, use the Windows executable through Wine.

If Delta Patcher reports a checksum mismatch, compare your clean source file to the matching row.

| Edition | Patch file | Clean source SHA-256 |
| --- | --- | --- |
| GOG 1.0.2.4 | `Tribal-Hunter-AP-GOG-1.0.2.4.xdelta` | `89a5a8049a8a2f23e179e836369899d8014d1ad99ec3a12d11d54fe1393766bb` |
| Steam build 15863961 | `Tribal-Hunter-AP-Steam-15863961.xdelta` | `d7615f1839507200d9adb295b3a19670f01ce0c05bd471034fdeab2326205859` |

With xdelta3, write a separate output first. This example uses the Steam patch. Substitute the GOG patch filename for a GOG copy. Once decoding succeeds, back up the copied folder's original `data.win` and rename `data.ap.win` to `data.win` in that folder.

```sh
xdelta3 -d -s data.win Tribal-Hunter-AP-Steam-15863961.xdelta data.ap.win
```

Both editions use the same AP world, YAML and connection steps.

## Generate and host

1. If someone else is hosting, edit the `name` in `Tribal-Hunter.yaml` and send the YAML to the host. Ask for the seed ID, server address and port, slot name, and room password if one is set.
2. If you are generating, use **Install APWorld** in the Archipelago Launcher and select `tribal_hunter_base.apworld`. Put your edited YAML and any other players’ YAMLs in the Archipelago `Players` folder.
3. Choose **Generate** in the launcher. Record the seed ID from the generated `AP_<seed ID>.zip` filename. Keep the ZIP with the session.
4. Use **Host** in the launcher to host locally, or upload the generated archive to the Archipelago hosting page and create a room there. Share the connection details and seed ID with each Tribal Hunter player.

See the [Archipelago setup guide](https://archipelago.gg/tutorial/Archipelago/setup_en) for local generation and hosting, or use the [Archipelago hosting page](https://archipelago.gg/uploads).

## Connect in Tribal Hunter

1. Before launching, open `ap-test.ini` in the modded game folder. Under `[world]`, replace `REPLACE_WITH_SEED_ID` with the generated seed ID. For example, if the output is `AP_123456789.zip`, enter `seed=123456789`. Close and reopen the game when switching seed IDs.
2. From the title screen, open **Settings → Archipelago**. Set **Server** to the host and port, **Slot** to the exact generated player name, and **Password** if the room has one. Use Enter to save each field. A local server on the default port uses `127.0.0.1:38281`. If the host supplies a `ws://` or `wss://` address, enter it as given.
3. Choose **Connect**. Once **AP connected** appears at the top right, back out to the title screen and press **F8** to start or resume your AP save. Saves are keyed to the seed ID and slot name.

If the connection fails, check the message inside the Archipelago menu. A wrong-seed message means the value in `ap-test.ini` differs from the server’s seed name. A slot refusal usually means the server, slot name, or password differs from what the host provided. If the slot settings are rejected, have the host check that they generated the room using this package’s AP world.

During play, **Pause → Collected Items** shows received rewards. Left/Right changes categories. Up/Down or the mouse wheel changes pages. The commented YAML explains the check pools, goals, and shortcut gate settings. The tracker can mirror the check pool settings and groups the ability unlock checks separately.
