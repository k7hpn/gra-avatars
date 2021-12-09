# default avatars.json

The `default avatars.json` file describes the configuration of avatar layers and how [The Great Reading Adventure](https://github.com/MCLD/greatreadingadventure) software imports the files present in the ZIP file containing avatar image elements.

The JSON file contains an `array` of Avatar Layer objects. An Avatar Layer object has a number of properties including arrays of `Texts`, `AvatarColors`, and `AvatarItems` objects (see below). Items specified in this file should match files present in the ZIP file.

Here are notes about the construction of the ZIP file:

- The top level of the ZIP file should contain the `default avatars.json` file.
- Two PNG files should also be present: `bundleicon.png` and `bundlenotif.png` should be 64x64 pixels PNG files allowing the user to select pre-packaged bundles and indicating that there are new bundles available, respectively.
- Each Avatar Layer object requires a folder in the same directory as the JSON file. The layer title should match the folder name, for example "Shirt".
- The Avatar Layer folder should contain an `icon.png` file which is 64x64 pixels and visually represents the avatar layer.
- The Avatar Layer folder will contain Avatar Item folders for each item that's available in the layer. For example, the "Shirt" folder might have folders in it named "ElizabethanShirt" and "ArgyleVestWithShirt").
- Item names (as presented in `default avatars.json`, the folder name, and Mission Control) are never shown to participants, they are just for management purposes.
- If the item does not have defined `AvatarColors`, the item's folder must contain:
  - `item.png` - 300x500 pixel transparent PNG - the layer item
  - `thumbnail.jpg` - 140x140 pixel JPG - a square thumbnail of the layer item
- If the item has `AvatarColors` defined, the item's folder must contain:
  - Files named matching the color specified in the `AvatarColors` records, e.g. if the Avatar Color's `Color` entry is "800080" then a 300x500 pixel transparent PNG named "800080.png" should be present.
  - `thumbnail.jpg` - 140x140 pixel JPG - a square thumbnail of the layer item

Here is a partial sample layout for the avatar ZIP file:

- `bundleicon.png`
- `bundlenotif.png`
- `default avatars.json`
- `Hair` - folder
  - `icon.png`
  - `pigtails` - folder
    - `thumbnail.jpg`
    - `800080.png`
- `Shirt` - folder
  - `icon.png`
  - `ArgyleVestWithShirt` - folder
    - `item.png`
    - `thumbnails.jpg`
  - `ElizabethanShirt` - folder
    - `item.png`
    - `thumbnail.jpg`

## Avatar Layer

- **Name** - _required_ - `string` - Name assigned to the layer (for management in Mission Control, not visible to participants), the folder associated with the layer needs the same name

- **Position** - _required_ - `int` - Layer order (z-index) of the avatar parts when combined, must be unique per layer

- **CanBeEmpty** - `True` or `False` - Sets whether an item must be present for the layer

- **GroupId** - _required_ - `int` - Grouping to display the layer selector in, combination of GroupId/SortOrder must be unique

- **SortOrder** - _required_ - `int` - Order within its group to display the layer selector, combination of GroupId/SortOrder must be unique

- **DefaultLayer** - `True` or `False` - Sets the layer to be selected by default when loading the avatar page, only one layer can be the default

- **ShowItemSelector** - `True` or `False` - Sets whether the item selector should be shown for the layer, only true if the layer contains multiple items

- **ShowColorSelector** - `True` or `False` - Sets whether the color selector should be shown for the layer, only true if the layer contains multiple colors

- **ZoomScale** - _required_ - `decimal` - Amount to zoom when viewing avatar selector on a mobile device: values > 1 zooms in, values < 1 zoom out

- **ZoomXOffset** - `int` - Amount to shift the y-axis when viewing avatar selector on a mobile device: positive values shift the view down, negative values shift the view up

- **Texts** - _required for each language_ - `array`

  - **Language** - _required_ - `string` - IETF BCP 47 language tag

  - **Name** - _required_ - `string` - Name to be displayed for the layer in the associated language

- **AvatarColors** - _required if layer uses colors_ - `array`

  - **Color** - _required_ - `string` - Hexadecimal color code to display in the color selector, the image corresponding with the color needs to be named the same

  - **SortOrder** _required_ - `int` - Order to display the color for the layer, must be unique within the layer

- **AvatarItems** - _required_ - `array`

  - **Name** - _required_ - `string` - Name assigned to the item (for management in Mission Control, not visible to participants), the folder associated with the item needs the same name

  - **SortOrder** - _required_ - `int` - Order to display the item for the layer - must be unique within the layer

  - **Unlockable** - `True` or `False` - True hides the item from the selector unless it's unlocked for a user through a trigger
