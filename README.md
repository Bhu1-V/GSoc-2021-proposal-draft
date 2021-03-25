# GSoc-2021-proposal-draft-Project_Stuff_Only.
This is a draft for the GSoc proposal of godot Organisation working on Command palette project.

## user scenarios
* user can search a command from the line-edit in thee command palette.
* user can execute a command that he searched.
* user can view shortcut for a command if available.
* user can search file or scene.
* user can view all the aviable commands with a fuzzy-search result.
* user can change workspace.

## Presentation and integration
* user uses a shortcut for command palette `ctrl + shift + p` or `cmd + shift + p` to open a [Modal-Dialog](https://en.wikipedia.org/wiki/Modal_window), Which has a line-edit to search and list-view that contains fuzzy-search result of the above searched command or file.
* [Modal-Dialog](https://en.wikipedia.org/wiki/Modal_window) mentioned doesn't have any close button and can be closed by either `Esc` button or changing the focus to other view.
* first retrieved search result is selected by default and pressing `return` or `enter` key would execute that command or open that scence or file.
  
  ### 1.Some Features
  * use `?` to get available command filters like :
      * `>` for editor commands. (Editor Main Menu Settings) 
      * ` `(prefixed with nothing) search for Resources.
   * Example:` >op ` will search and retrieve all the commands with name containing `op`.
  
  * Navigate Workspace (2D, 3D, Script, AssetLib).
  
  ### 2.Dependencies
     #### [Modal-Dialog :](https://en.wikipedia.org/wiki/Modal_window)
          Should use available GUI to make something like described in Wiki.
     #### List-View :
          May be I can use popup-menu but should think of something else.
  
## Architecture - [might change]

![Cmd-plt (1)](https://user-images.githubusercontent.com/70578657/112489501-80345b80-8da4-11eb-8f88-db01d26bccd2.png)
Flow :
![cmd-plt-flow](https://user-images.githubusercontent.com/70578657/112496032-6dbd2080-8daa-11eb-8118-2820cf74a83f.png)



## Visual
 
 Complete Picture:

 ![cmd-plt-visual](https://user-images.githubusercontent.com/70578657/112499170-3bf98900-8dad-11eb-9550-0708309ca8ed.png)

 ![complete-cmd-visual](https://user-images.githubusercontent.com/70578657/112501369-32712080-8daf-11eb-9edd-381bbfecf8b2.png)
