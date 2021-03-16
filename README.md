# GSoc-2021-proposal-draft
This is a draft for the GSoc proposal of godot Organisation working on Command palette project. [Just-Project-Stuff.]

## user scenarios
* user can search a command from the line-edit in thee command palette.
* user can execute a command that he searched.
* user can view shortcut for a command if available.
* user can search file or scene.
* user can view all the aviable commands with a fuzzy-search result.

## Presentation and integration
* user uses a shortcut for command palette `ctrl + shift + p` or `cmd + shift + p` to open a [Modal-Dialog](https://en.wikipedia.org/wiki/Modal_window), Which has a line-edit to search and list-view that contains fuzzy-search result of the above searched command or file.
* [Modal-Dialog](https://en.wikipedia.org/wiki/Modal_window) mentioned doesn't have any close button and can be closed by either `Esc` button or changing the focus to other view.
* first retrieved search result is selected by default and pressing `return` or `enter` key would execute that command or open that scence or file.
  
  ### 1.Some Features
  * use `?` to get available command filters like :
      * `>` for editor commands. (Editor Main Menu Settings) 
      * `$` search for scenes.
      * `#` search for scripts.
   * Example:` $ma ` will search and retrieve all the scene with name containing `ma`.
  
  * Navigate Workspace (2D, 3D, Script, AssetLib).
  
  ### 2.Dependencies
     #### [Modal-Dialog :](https://en.wikipedia.org/wiki/Modal_window)
          Should use available GUI to make something like described in Wiki.
     #### List-View :
          May be I can use popup-menu but should think of something else.
  
## Architecture - [might change]



## Visual
