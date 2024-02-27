# PiggyCrates [![Poggit-CI](https://poggit.pmmp.io/shield.dl/PiggyCrates)](https://poggit.pmmp.io/p/PiggyCrates) [![Discord](https://img.shields.io/discord/330850307607363585?logo=discord)](https://discord.gg/66j9cFm6Cc)

PiggyCrates is a simple and customizable crates plugin, supporting an unlimited amount of crate types. It also supports
vanilla and custom enchants, such as [PiggyCustomEnchants](https://github.com/DaPigGuy/PiggyCustomEnchants/).

## Voraussetzungen

* Grundkenntnisse zur Installation von Plugins von Poggit Releases und/oder Poggit CI 
* PMMP 4.9.9 :D

## Installation und Einrichtung

1. Installieren Sie das Plugin von Poggit.
2. Starten Sie Ihren Server.
3. (Optional) Die Datei „config.yml“ enthält einige Optionen, mit denen Sie Ihre wichtigsten Elemente und Kistenmodi anpassen können (Standard).
   ist Roulette).
4. Öffnen Sie „crates.yml“.
5. PiggyCrates unterstützt eine unbegrenzte Anzahl von Kisten. Um eine Kiste zu definieren, fügen Sie einen Schlüssel „crates.yourcratename“ hinzu.
6. Konfigurieren Sie Ihre Kistentypen. Kistentypen haben verschiedene Eigenschaften:
    * (Optional) „floating-text“: Schwebender Text, der über dem Crate-Typ angezeigt wird. Lassen Sie das Feld leer, um keinen schwebenden Text zu erhalten.
    * (Optional) „Befehle“: Befehle, die von CONSOLE ausgeführt werden sollen, wenn der Crate-Typ geöffnet wird. Verwenden Sie „{PLAYER}“ als Platzhalter
      für Spielernamen.
    * „Drops“: Mögliche Drops eines Kistentyps. Elemente werden mit den Eigenschaften definiert:
        * `id`: Artikel-ID
        * „Meta“: Element-Meta
        * „Betrag“: Artikelbetrag
        * (Optional) „Typ“: Artikeltyp
            * (Standard) „item“: Führt alle Crate-Item-Befehle aus und gibt den Artikel aus
            * „Befehl“: Führt alle Crate-Item-Befehle aus
        * (Optional) „Chance“: Artikelgewicht
        * (Optional) „nbt“: Element NBT als stringifiziertes JSON
        * (Optional) „Name“: Artikelname
        * (Optional) „lore“: Item Lore als String mit Zeilenumbrüchen, dargestellt als „\n“.
        * (Optional) „Verzauberungen“: Gegenstandsverzauberungen, die wie folgt definiert sind:
          „yaml
          Verzauberungen:
           -name: „Schutz“
             Level 1
           -Name: „Dornen“
             Level 1
          „
        * (Optional) „Befehle“: Befehle, die von CONSOLE ausgeführt werden sollen, wenn das Element von der Kiste abgelegt wird.
    * „Betrag“: Anzahl der Tropfen, die ein einzelner Kistentyp gibt.

   **Example**:
   ```yaml
   crates:
     # Crate type named "Example"
     Example:
       floating-text: "Example Crate"
       amount: 1
       # Will run the command "/say" when opened
       commands:
         - "say {PLAYER} has opened the example crate!"
       drops:
         # 50% chance for 1x Diamond Sword named Sharpened Diamond Sword w/ Sharpness 5 enchantment
         # Will run the command "/tell" on drop
         - id: 276
           meta: 0
           amount: 1
           chance: 50
           name: "Sharpened Diamond Sword"
           enchantments:
             - name: "Sharpness"
               level: 5
           commands:
             - "tell {PLAYER} You got a Sharpened Diamond Sword! ;o"
         # Identical to the above drop but with a 25% chance and an Iron Sword
         - id: 267
           meta: 0
           amount: 1
           chance: 25
           name: "Sharpened Iron Sword"
           enchantments:
             - name: "Sharpness"
               level: 5
           commands:
             - "tell {PLAYER} You got a Sharpened Iron Sword! ;o"
         # 25% chance for player to get money
         - id: 266
           meta: 0
           amount: 1
           chance: 25
           name: "$2500"
           type: command
           commands:
             - "givemoney {PLAYER} 2500"
    ```
7. Restart your server.
8. Connect to your server.
9. Place a chest block where you intend on having a crate.
9. Run the command `/crate <crate name>`
10. Tap the target chest.
11. Repeat with other crate types.
12. You're done!

## Commands

| Command | Description | Permissions | Aliases
| --- | --- | --- | --- |
| `/crate <crate>` | Changes a chest to a crate by tapping | `piggycrates.command.crate` | N/A |
| `/key` | Gives a player a specific crate key | `piggycrates.command.key` | N/A |
| `/keyall` | Gives all online players a specific crate key | `piggycrates.command.keyall` | N/A |

## Permissions

| Permissions | Description | Default |
| --- | --- | --- |
| `piggycrates` | Allows usage of all PiggyCrates features | `false` |
| `piggycrates.command` | Allow usage of all PiggyCrates commands | `op` |
| `piggycrates.command.crate` | Allow usage of all /crate commands | `op` |
| `piggycrates.command.key` | Allow usage of the /key command | `op` |
| `piggycrates.command.keyall` | Allow usage of the /keyall command | `op` |

## Issue Reporting

* If you experience an unexpected non-crash behavior with PiggyCrates,
  click [here](https://github.com/DaPigGuy/PiggyCrates/issues/new?assignees=DaPigGuy&labels=bug&template=bug_report.md&title=)
  .
* If you experience a crash in PiggyCrates,
  click [here](https://github.com/DaPigGuy/PiggyCrates/issues/new?assignees=DaPigGuy&labels=bug&template=crash.md&title=)
  .
* If you would like to suggest a feature to be added to PiggyCrates,
  click [here](https://github.com/DaPigGuy/PiggyCrates/issues/new?assignees=DaPigGuy&labels=suggestion&template=suggestion.md&title=)
  .
* If you require support, please join our discord server [here](https://discord.gg/qmnDsSD).
* Do not file any issues related to outdated API version; we will resolve such issues as soon as possible.
* We do not support any spoons of PocketMine-MP. Anything to do with spoons (Issues or PRs) will be ignored.
    * This includes plugins that modify PocketMine-MP's behavior directly, such as TeaSpoon.

## License

```
   Copyright 2018-2020 DaPigGuy

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

```
