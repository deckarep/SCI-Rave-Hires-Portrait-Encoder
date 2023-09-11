# Sierra RIVE Encoder

For fellow Sierra and fans of the original King's Quest Adventure games this utility is the first of its kind (to my 
knowledge) that allows a person to edit/modify/create brand new RIVE encoded hires talking/animated
portraits for the game King's Quest 6.

## Demo Time!

Things you can currently do:

- Modify existing character portraits
- Modify existing character color palettes
- Create entirely new characters (based off existing characters)

Things you can't yet do:

- Modify lip-sync data
- Create new mouth/facial movements
- Go beyond 256 colors - a limitation of the original game not this utility.

## How it works

A new character `.json` definition file must be created and you must additionally include the original game BIN
file assets in a directory named `Originals`. These files are needed because the lip-sync data is pulled from
these files which will be fully compatible with your new character and the game.

A reference character has been built in the folder: `Characters/KingGraham` that matches the original dimensions
and voice movements. If an original game character had `16` images, your new character must have `16` matching images
but the placement and sizing of these images can vary so long as they fit within the primary portrait dimensions of
`112 Width x 154 Height`. This is currently mandatory because the game expects portraits in this size however the size
and placement of the overlay images can be different from the original.

Therefore to create an entirely new character you need to:

- Create a new directory in `Characters/<char-name>/`
- Create a new .json definition file
- Create a fresh set of `.png` images of the correct dimensions
- Run the command

## Running the command

Currently the tool requires the Go SDK. If there is interest/demand, i'll provide a downloadable tool that requires no 
developer tools to be installed.

Simply point the utility to the appropriate `JSON` file in the appropriate directory and be sure that you have placed the 
same original `BIN` files in the `Originals/` folder. This requires that you have your own copy of Hires version of 
King's Quest 6 where the original files can be found in a folder called: `ACTORS/`. Without these original `.BIN` files
this script will error out.

Once everything is setup you can run the command like so:

```go
go run main.go Characters/KingGraham/GRAHAM.json
```

## Credits

This utility was only possible by referencing the RAVE file-format documented in the SCUMMVM implementation. Many thanks
goes to the original contributors to SCUMMVM and the FreeSCI project who took to the time to reverse engineer Sierra's
great gaming legacy.

If the command runs with no errors you should see a file generated in the character folder called: 
`<character-name_GEN.BIN>`. Which can be place in your version of KQ6 actors folder. Be sure to overwrite the existing
character or the new file will not be used by the game.


