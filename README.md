# GSoc-2021-proposal-draft
This is a draft for the GSoc proposal for godot Organisation working on Command palette project.

## user scenarios
* user can search a command from the line-edit in thee command palette.
* user can execute a command that he searched.
* user can view shortcut for a command if available.
* user can search file or scene.
* user can view all the aviable commands with a fuzzy-search result.

## Presentation and integration
* user uses a shortcut for command palette `ctrl + shift + p` or `cmd + shift + p` to open a [Modal-Window](https://en.wikipedia.org/wiki/Modal_window), Which has a line-edit to search and list-view that contains fuzzy-search result of the above searched command or file.
* [Modal-Window](https://en.wikipedia.org/wiki/Modal_window) mentioned doesn't have any close button and can be closed by either `Esc` button or changing the focus to other view.
* first retrieved search result is selected by default and pressing `return` or `enter` key would execute that command or open that scence or file.
  
  ### some features
  * use `?` to get available command filters like :
      * `>` for editor commands.
      * `$` search for scenes.
      * `#` search for scripts.
       
  * Example:` $ma ` will search and retrieve all the scene with name containing `ma`.
