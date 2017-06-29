# OMO
Kotlin port with changes and improvements for omo originally by ForeignGuyMike

# Changes

Following is changes from original project

* Support running on PC for any resolution (also support wide-screen)
* Buildable on iOS via MOE
* Fixed transition effect between game state to applies to whole screen
* Fixed touch checking for any screen resolution (via `unproject()` with specified of current `Viewport`'s width and height)
* Slightly better organization of `Tile` class spanning into
    * `SizingTile` for use as normal tile in gameplay session
    * `GlowTile` for use as tile effect when touch on tile to select it, it includes ability to set type of do contracting effect as well
    * `ExpandingTile` for use as transitioning effect when switch between one game state to another
* Flexible touch to select/deselect tiles via dragging. Support up to 2 fingers at the same time
* Save save to save highscore for each difficulty
* Added support for rendering space, + (plus), and - (minus) symbol from spritesheet
* Safer using of score to save as highscore (if beaten), and supply in Score screen
    
# Kotlin notices

Interesting points to look at regarding Kotlin language features used in the project

* Make use of `Array` initialization with initializing function that uses `also` to reduces line of code and manual two-for-loop iteration into just technically 1 line of code.
* Use `forEach` whenever possible
* 2 dimensional array declaration i.e. `Array<Array<ExpandingTile>>`
* `open class` to allow other classes to extend it i.e `Tile` class
* Customized getter function for class's properties that not just return its backing field but involves condition checking to return `Boolean`

# libgdx notices

Interesting points to look at regarding to libgdx

* Multiple Cameras and Viewports to achieve rendering normal game state's content, and transition effect together at the same time. Lesson learned, don't forget to call `Viewport.apply()` for your current active Viewport before rendering with `SpriteBatch` to make such Viewport active.
* Use both `FitViewport` for gameplay content, and `ExtendViewport` for transition effect (whole screen)
* `Camera.unproject()` that applies screen width, and hieght from specified `Viewport` making resolution independence when check touching position

# License

[MIT](https://github.com/haxpor/omo/blob/master/LICENSE), Wasin Thonkaew  
You should not just use code in this project, and make a copy of game to publish. Please note that ForeignGuyMike published his original idea (OMO) to [Google Play](https://play.google.com/store/apps/details?id=com.distraction.omo.android&pageId=105950263560359459987).

You can use the code, adapt it into your own project, or modify the game further with different game design etc so it's not complete rip-off, then you are clear to publish the game.
