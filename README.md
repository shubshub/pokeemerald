# emerald-180

Pokémon Emerald with the overworld rotated a perfect 180°. This is a fork of [pret/pokeemerald](https://github.com/pret/pokeemerald), and the game itself is untouched: the same maps, scripts, trainers, warps and cutscenes. Only the picture is rotated, along with the D-pad, so pressing Up still moves you up the screen (which is south on the map). Text boxes, menus and the other screens (battles, bag, party and so on) stay upright.

The rotation happens at render time and is switched by `ROTATE_OVERWORLD_180` in [include/config.h](include/config.h). Comment it out to build the original game.

* [src/field_camera.c](src/field_camera.c) draws each map metatile at the mirrored spot in the map's tilemaps with its tiles flipped both ways, and mirrors the map scroll.
* [src/sprite.c](src/sprite.c) mirrors the overworld's sprites around the centre of the screen and flips them (affine sprites get their matrix negated). This covers people, the player, field effects and weather; sprites drawn over text boxes stay upright.
* [src/main.c](src/main.c) rotates the D-pad for walking, biking and surfing.

Build it as described in [INSTALL.md](INSTALL.md). With the rotation on, `pokeemerald.gba` no longer matches the original's sha1; with it commented out, `make compare` still passes.

Every push to master is also built by the [Build ROM](.github/workflows/build.yml) GitHub Actions workflow: open the run in the Actions tab and download the `emerald-180` artifact, which contains `emerald-180.gba`.

Not rotated (yet): the region map, Fly map and PokéNav map; placing secret base decorations; the map shown behind the Poké Mart buy menu; battle transition effects; and the Deoxys rock and Mirage Tower cutscene effects.

---

# Pokémon Emerald

This is a decompilation of Pokémon Emerald.

It builds the following ROM:

* [**pokeemerald.gba**](https://datomatic.no-intro.org/index.php?page=show_record&s=23&n=1961) `sha1: f3ae088181bf583e55daf962a92bb46f4f1d07b7`

To set up the repository, see [INSTALL.md](INSTALL.md).

For contacts and other pret projects, see [pret.github.io](https://pret.github.io/).
