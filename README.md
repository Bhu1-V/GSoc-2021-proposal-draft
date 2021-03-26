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
  
## Architecture 
#### Priliminaries :
  1.Commands / Actions : It is a reference of Callable(Function pointer) that calls some specific function when executed.
  
To Have a Functional Command Palette we need :

   1. A Data-Structre to Store Callable and Arguments and Retreive it by some string.
       
       A `EditorActions` Class is made and Store actions with a HashMap where String type as Key and Storing a Pair of Callable and Vector<Variant> for arguments (`HashMap<String, Pair<Callable, Vector<Variant>> callables`). but EditorAction has some other big plans [#70](https://github.com/godotengine/godot-proposals/issues/70). So to make a difference between Command Palette actions and other Editor actions we have a `Vector<String> palette_action` which keep track of all Command palette actions. and another Hashmap for shortcuts
  `HashMap<String, Shortcut>`.
  
  2. Register EditorActions.
    
      So this can be done in `EditorNode` where most of the Editor code lies. where i call `EditorAction::add_palette_action("action_name", callable_mp(this, func), varray(arg1,arg2..), [Shortcut]);`. 
  
  
  3. We need a way to search and execute for a Command from avaiable commands.
  
      A `CommandPalette` Class is made which contains all the UI like line-edit, List-view. when we start searching something if it's start with `>` it will start searching EditorAction commands i.e it will retreive action_names from `EditorActions::palete_actions` otherwise it will just Search for Resource just like `Quick Open Resource`. when Desired action is selected it emits `execute_command` signal or `open_file` in case of resource.
  
  4. Execute the Command once the desired command is selected.
  
      So `execute_command` signal is connected to `EditorNode::_execute_command()` which just calls `EditorAction::_execute_action(selected_command)` and `open_file` signal connects to `EditorNode::_open_file()` which opens file same as `Quick Open Resource`.
      
Incomplete but Working ProtoType: 
![NBYS1r74FW](https://user-images.githubusercontent.com/70578657/112581454-7a7a5c80-8e1c-11eb-98ba-0902c4cc4601.gif)



![Cmd-plt (1)](https://user-images.githubusercontent.com/70578657/112489501-80345b80-8da4-11eb-8f88-db01d26bccd2.png)
Flow :
![cmd-plt-flow](https://user-images.githubusercontent.com/70578657/112496032-6dbd2080-8daa-11eb-8118-2820cf74a83f.png)



## Visual
 
 Complete Picture:

 ![cmd-plt-visual](https://user-images.githubusercontent.com/70578657/112499170-3bf98900-8dad-11eb-9550-0708309ca8ed.png)

 ![complete-cmd-visual](https://user-images.githubusercontent.com/70578657/112501369-32712080-8daf-11eb-9edd-381bbfecf8b2.png)
