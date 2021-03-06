# Cinder-poSpritesheet

[Potion's](http://www.potiondesign.com) spritesheet block for [Cinder](http://libcinder.org). Cinder-poSpritesheet is released under the [BSD New License](./LICENSE).

## Using this Repo

When pulling down the repo, `develop` is the latest branch, `master` is stable. If you're using in conjunction with [poScene](../Cinder-poScene), make sure you're on poScene v2. If you're on poScene v1, you can check out the `v1.0` tag. If you're on an old project with Cinder 0.8.6, you can checkout the `v0.8.6` tag.

## Using the Block

The block consists of two classes:

- **Spritesheet:** parses and keeps track of the frame data
- **SpritesheetAnimation:** provides control for frame playback

Tested on OS X Yosemite and Windows 8.

## Features 
- Supports spritesheets created with [TexturePacker](https://www.codeandweb.com/texturepacker)
- JSON (Array), XML (generic) data formats from within [TexturePacker](https://www.codeandweb.com/texturepacker)
- Multipacked textures
- Play, pause, stop, loop, reverse animation
- Set animation frame rate
- Get signal when animation has finished playing

*Currently doesn't support rotated sprites.*

## Samples
- **SpritesheetFrame:** draws a spritesheet frame based on mouse position
- **SpritesheetAnimation:** animates spritesheet frames across the app window

> [goblin](http://opengameart.org/content/goblin) by [Clint Bellanger](http://opengameart.org/users/clint-bellanger) used under [Creative Commons Attribution (CC-BY) 3.0 License](http://creativecommons.org/licenses/by/3.0/) / Scaled up from original.

## Getting started

To draw a specific frame from the spritesheet:

```C++
gl::TextureRef texture = gl::Texture::create(loadImage(loadAsset("goblin.png")));
JsonTree json = JsonTree(loadAsset("goblin.json"));
	
mSpritesheet = po::Spritesheet::create(texture, json);

//	draw frame by number
mSpritesheet->drawFrame(6);

// frame by source filename
mSpritesheet->drawFrame("0031.png");
```

To animate the spritesheet:

```C++
gl::TextureRef texture = gl::Texture::create(loadImage(loadAsset("charge.png")));
JsonTree json = JsonTree(loadAsset("charge.json"));
	
mSpritesheet = po::Spritesheet::create(texture, json);
mSpritesheetAnimation = po::SpritesheetAnimation::create(mSpritesheet);
mSpritesheetAnimation->play();
```
