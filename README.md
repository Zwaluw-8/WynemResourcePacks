# Wynem Resource Packs
This repository contains a list of resource packs that are available through the [Wynem Discord bot](https://wynem.com/) as custom Minecraft asset versions. Anyone using the bot can browse the texture files of any pack listed here.

## Submitting Resource Packs
Anyone can submit resource packs to this repository as long as the pack meets all of the following requirements:
1. You must have full permission from the pack author to put the pack on the bot
2. The pack must be of a high quality, and change a substantial amount of the textures in the game
3. The pack must be hosted on either GitHub or Modrinth
4. The pack must not share a name with any past, present, or future Minecraft version

Important: I have the final say on whether a pack is accepted, even if it meets all of the above criteria.

## How to Submit
1. Open the `resourcepacks.json` file in this repository
2. Add your pack to the list using one of the formats below
3. Open a pull request, and demonstrate that you have permission to add the pack (if required)

## JSON Format
Every pack is identified by a key (the pack ID) and must declare exactly one source: either `github` or `modrinth`.

### GitHub-hosted packs
```js
"pack_id": {
  "github": ["owner", "repo"]
}
```
The `owner` and `repo` are taken straight from the repository URL: `https://github.com/<owner>/<repo>`. The default branch is detected automatically, so you do not need to specify it.

### Modrinth-hosted packs
```js
"pack_id": {
  "modrinth": "projectId"
}
```
To get the project ID, open the resource pack page on Modrinth, click the three dots next to the download button, and select **Copy ID**.

<img src="https://raw.githubusercontent.com/ewanhowell5195/WynemResourcePacks/main/images/modrinth.png">

### Optional fields
- `alias`: an alternate ID that resolves to this pack
- `name`: a display name. Defaults to the pack ID with underscores replaced by spaces and converted to title case

## Updating Packs
Updates are detected automatically. Once an hour, the bot checks each pack's source for changes:
- **GitHub**: compares the latest commit SHA on the default branch
- **Modrinth**: compares the latest version ID

If something has changed, the pack is re-downloaded the next time it is used. No manual action is required after pushing an update.
