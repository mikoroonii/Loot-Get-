# Loot Get!

Loot Get is a free, open source, interactive Twitch overlay for viewers to play while they watch.

# Setup:

### Configuration

In the same folder as the game exe, there are some more files. The one we're currently interested in is "Config.txt".
It looks a bit like this:

```
[
    {
        "channel": "",
        "user": "",
		"cooldown": 0
    }
]
```

The first thing you need to do is fill out these fields.
In between the two quotation marks is where you need to put in your info.

- Channel
  - This is the channel that Loot Get will be connecting to.
- User
  - This is the user that Loot Get will be sending messages from.
    **[IMPORTANT!]** this MUST be the same account that you authenticate with later.
- Cooldown
  - This is the amount of time (in seconds) that users must wait until they can open another crate.

## Running the game

Immediately each time you run the game, a browser window should open. Ensure that your browser is logged in with the correct twitch account (the one set as "User" in config.txt) and continue through the prompts. Once connected, the game should send a message in your chat saying "Connected to Loot Get!". If this message doesn't appear, there has been some sort of misconfiguration during setup. Double check everything and try again. Please note that the window will be invisible until someone spins the carousel.

### Twitch Commands

- !spin
  - Spins the carousel, activating the game. This is what users will type to participate, and will be influenced by the cooldown.
- !score
  - Returns the total "score" of the user that sends the command.

## Expandability

All items in the game can be removed, modified, replaced or otherwise changed to fit your needs, or you can add your own.

### Rarities

in the "Items" folder are 5 more folders. These correspond to the "rarity" of the given items. Inside each folder, by default, is one item, but you can put as many as you want in each of them. The chances are below.

- **Common**: 30%
- **Uncommon**: 25%
- **Rare**: 20%
- **Epic**: 15%
- **Legendary**: 5%

The randomizer will first pick a rarity based on these chances, and then pick a random item in that rarity folder. The value will be set to a random number between the items valuemin and valuemax properties defined in its json.

### Creating an item

An item needs the following data

1.  a 3D model of the item in the OBJ format with the same name as the folder. (with MTL file and textures in the correct place relative to the obj) please note that the item MUST use textures in order to work, and does not support vertex colors or color materials.
2.  an icon for the item in PNG format (recommended 128px and transparent)
3.  a JSON file with the same name as the folder (template below)

```
[
{
    "name": "Glock",
    "valuemax": 30,
    "valuemin": 15,
    "description": "Just a glock. not that crazy",
    "tags": []
}
]
```

### Tags

This feature is not yet implemented, but it will be. An item will be able to have optional tags (eg custom sounds, visual effects, animations) that will be defined in the JSON file. Right now the "Tags" field will just be empty and can be removed completely if you wish.

## OBS Config

![OBS Config](https://cdn.mikoroonii.com/ShareX/2024/05/obs64_OLTkacyhoQ.png)
