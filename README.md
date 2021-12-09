# Great Reading Adventure Avatars

This repository contains the files used to create the default avatar package for [The Greating Reading Adventure](https://github.com/mcld/greatreadingadventure) online reading program software.

The majority of the avatar artwork originated in [Glitch the Game](https://www.glitchthegame.com/public-domain-game-art/) and was used via their [Creative Commons CC0 1.0 Universal License](http://creativecommons.org/publicdomain/zero/1.0/legalcode).

Additional items are added (usually to support the [Maricopa County Reads](https://maricopacountyreads.org/) summer reading program managed by the [Maricopa County Library District](https://mcldaz.org/) who manages this package and The Great Reading Adventure software.)

## Usage

When using a release of The Great Reading Adventure, importing the default avatars in Mission Control will import the avatars from this collection.

## Using custom avatars

The default avatar package includes over 5,500 elements. If the desire is to use custom avatars in place of the default avatars, the software can accept and layer 300x500 pixel `.PNG` files. For information on how to configure a `.ZIP` archive so it can be imported into the GRA, see the documentation in [default avatars.md](default%20avatars.md).

The default GRA stylesheet includes cropping based on the way the default avatars display, for example: on mobile devices the only part of the avatar which shows is the head and head accessories. If you are using custom images and want to override the default cropping, add the following to `content/site1/styles/site.css` file in the shared directory:

```css
.avatar-container-dashboard {
  height: 400px;
}

@media only screen and (min-width: 768px) {
  .avatar-container-dashboard {
    height: 250px;
  }
}

@media only screen and (min-width: 992px) {
  .avatar-container-dashboard {
    height: 350px;
  }
}

@media only screen and (min-width: 1200px) {
  .avatar-container-dashboard {
    height: 425px;
  }
}
```

## License

Much like the original art from Glitch the Game, art in this repository is licensed under the [Creative Commons CC0 1.0 Universal License](https://github.com/MCLD/gra-avatars/blob/main/LICENSE).
