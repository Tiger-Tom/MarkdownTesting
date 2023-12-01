# `RunServer` (imported as `RS`)
> None
# `Bootstrapper` (shorthand: `RSBS`)

## access_entrypoint(...*1)
```python
method access_entrypoint(ep: str) -> types.ModuleType
```
> Loads the entrypoint's surrounding module

## bootstrap(...*1)
```python
method bootstrap(close_after: bool = True)
```
> Executes the base manifest, then accesses, assigns, and chainloads the entrypoint

## chainload_entrypoint(...*1)
```python
method chainload_entrypoint(rs: Callable)
```
> Runs the entrypoint's __call__ method

## close(...*1)
```python
method close(do_exit: bool | int = False)
```
> Executes all shutdown callbacks and closes logging (logging.shutdown()), and exits with exit code do_exit if it isn't False

## ensure_python_version()
```python
classmethod ensure_python_version()
```
> Ensure that the Python version meets the minimum requirements

## parse_arguments(...*1)
```python
method parse_arguments(args=None)
```
> Generate and ArgumentParser and parse (known) arguments

## register_onclose(...*1)
```python
method register_onclose(cb: Callable)
```
> Registers a function to run when self.close() is called

## run_base_manifest()
```python
method run_base_manifest()
```
> Executes the base manifest (_rsruntime/MANIFEST.ini)

## setup_logger()
```python
method setup_logger() -> logging.Logger
```
> Sets up self.logger, as well as logging.INFOPLUS/IRRECOVERABLE and Logger.infop/irrec()

## stage_entrypoint(...*1)
```python
method stage_entrypoint(rs_outer: types.ModuleType) -> rs_outer.RunServer
```
> Initializes the entrypoint's class (with self as an argument)
# `Util` (shorthand: `RSU`)
# `Flags` (shorthand: `RSF`)
# `Config` (shorthand: `RSC`)

## bettergetter(...*3)
```python
method bettergetter(<details><summary>...</summary>
    key: Key, default: Union = Behavior.RAISE, set_default: bool = True
</details>) -> Union
```
> Gets the value of key
>     If the key is missing, then:
>         if default is Behavior.RAISE: raises KeyError
>         otherwise: returns default, and if set_default is truthy then sets the key to default

## close()
```python
method close()
```
> <no doc>

## contains(...*2)
```python
method contains(<details><summary>...</summary>
    key: Key, _tree: Optional = None
</details>) -> bool
```
> Returns whether or not the key exists

## get(...*3)
```python
method get(<details><summary>...</summary>
    key: Key, default: Union = Behavior.RAISE, _tree: Optional = None
</details>) -> Deserialized
```
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

## get(...*3)
```python
method get(<details><summary>...</summary>
    key: Key, default: Union = Behavior.RAISE, _tree: Optional = None
</details>) -> Deserialized
```
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

## is_autosyncing()
```python
method is_autosyncing() -> bool
```
> Returns whether or not the internal watchdog timer is ticking

## items_full(...*2)
```python
method items_full(<details><summary>...</summary>
    start_key: Key, key_join: bool = True
</details>) -> Generator
```
> Iterates over every (key, value) pair, yielding the entire key

## items_short(...*1)
```python
method items_short(start_key: Key)
```
> Iterates over every (key, value) pair, yielding the last part of the key

## key(...*2)
```python
classmethod key(<details><summary>...</summary>
    key: Key, top_level: bool = False
</details>) -> tuple
```
> Transform a string / tuple of strings into a key

## keys(...*2)
```python
method keys(<details><summary>...</summary>
    start_key: Key | None = None, key_join: bool = True
</details>) -> Generator
```
> Iterates over every key

## mass_set_default(...*3)
```python
method mass_set_default(<details><summary>...</summary>
    pfx: str | None = None, dict_vals: dict[str, Serializable] | None = None, values: Serializable
</details>)
```
> Sets a large amount of default values
>     When pfx is not None, it is prepended (with a / if it doesn't already have one) to each key
> Values are either given through dict_vals or **values (keyword args)
>     Using both is probably bad but not prohibited
>         A SyntaxWarning shall be issued upon you to remind you of your choices.
>     If a value is in both and is not the same, a ValueError is raised
>         Once this has been checked, they are merged together
> If a total of 0 values are given, an error is logged
> Otherwise, an info is logged decribing how many keys will be set

## path_from_topkey(...*1)
```python
method path_from_topkey(topkey: str)
```
> Returns the Path corresponding to the top-key's file

## readin(...*1)
```python
method readin(topkey: str)
```
> Reads in a top-level key

## readin_modified()
```python
method readin_modified()
```
> Reads in top-level keys that have been changed

## set_default(...*2)
```python
method set_default(<details><summary>...</summary>
    option: str | tuple[str], value: Serializable
</details>)
```
> Sets an option if it does not exist

## setitem(...*3)
```python
method setitem(<details><summary>...</summary>
    key: Key, val: Serializable, _tree: Optional = None
</details>)
```
> Sets a key to a value

## sort(...*1)
```python
method sort(by: Callable = <lambda>)
```
> Sorts the data of this INIBackedDict in-place, marking all touched sections as dirty

## start_autosync()
```python
method start_autosync()
```
> Starts the internal watchdog timer

## stop_autosync()
```python
method stop_autosync()
```
> Stops the internal watchdog timer

## sync()
```python
method sync()
```
> Convenience method for writeback_dirty and readin_modified

## values(...*1)
```python
method values(start_key: Key) -> Generator
```
> Iterates over every value

## writeback(...*3)
```python
method writeback(<details><summary>...</summary>
    topkey: str, only_if_dirty: bool = True, clean: bool = True
</details>)
```
> Writes back a top-level key

## writeback_dirty()
```python
method writeback_dirty()
```
> <no doc>
# `ExceptionHandlers` (shorthand: `RSEH`)

## hookin()
```python
method hookin()
```
> <no doc>

## hookout()
```python
method hookout()
```
> <no doc>

## register_exception_hook(...*1)
```python
method register_exception_hook(callback: Callable)
```
> <no doc>

## register_thread_exception_hook(...*1)
```python
method register_thread_exception_hook(callback: Callable)
```
> <no doc>

## register_unraisable_hook(...*1)
```python
method register_unraisable_hook(callback: Callable)
```
> <no doc>
# `MCLang` (shorthand: `RSL`)

## extract_lang()
```python
method extract_lang() -> dict
```
> Extracts the language file from a server JAR file, sets and returns self.lang

## lang_to_pattern(...*3)
```python
method lang_to_pattern(<details><summary>...</summary>
    lang: str, group_names: tuple[str, ...] | None = None, prefix_suffix: str = ^{}$
</details>) -> Pattern
```
> <no doc>

## strip_prefix(...*1)
```python
method strip_prefix(line: str) -> tuple
```
> <no doc>
# `LineParser` (shorthand: `RSLP`)

## handle_line(...*1)
```python
method handle_line(line: str)
```
> <no doc>

## register_callback(...*3)
```python
method register_callback(<details><summary>...</summary>
    patt: Pattern, callback: Union, with_prefix: bool = True
</details>)
```
> Registers a callback
>     If keep_prefix, then lines that have the prefix are passed. callback should have the signature: `callback(match: re.Match, prefix: re.Match, t: time.struct_time)`
>     Otherwise, lines that don't have a prefix are passed; the callback should have the signature: `callback(match: re.Match)`

## register_chat_callback(...*1)
```python
method register_chat_callback(callback: Callable)
```
> Registers a callback for when chat is recieved
>     The callback should have the signature `callback(user: RS.UserManager.User, message: str, insecure: bool)`
# `PluginManager` (shorthand: `RSPM`)

## early_load_plugins()
```python
method early_load_plugins()
```
> <no doc>

## load_plugins()
```python
method load_plugins()
```
> <no doc>

## restart()
```python
method restart()
```
> <no doc>

## start()
```python
method start()
```
> <no doc>
# `ServerManager` (shorthand: `RSSM`)

## preferred_order()
```python
classmethod preferred_order() -> list
```
> <no doc>

## register(...*1)
```python
classmethod register(manager_type: Type)
```
> <no doc>
# `UserManager` (shorthand: `RSUM`)

## close()
```python
method close()
```
> <no doc>
# `TellRaw` (shorthand: `RSTR`)

## append(...*2)
```python
staticmethod append(<details><summary>...</summary>
    self, object
</details>)
```
> Append object to the end of the list.

## clear(...*1)
```python
staticmethod clear(self)
```
> Remove all items from list.

## copy(...*1)
```python
staticmethod copy(self)
```
> Return a shallow copy of the list.

## count(...*2)
```python
staticmethod count(<details><summary>...</summary>
    self, value
</details>)
```
> Return number of occurrences of value.

## extend(...*2)
```python
staticmethod extend(<details><summary>...</summary>
    self, iterable
</details>)
```
> Extend list by appending elements from the iterable.

## ijoin(...*2)
```python
staticmethod ijoin(<details><summary>...</summary>
    self, tellraws: tuple
</details>) -> Generator
```
> <no doc>

## index(...*4)
```python
staticmethod index(<details><summary>...</summary>
    self, value, start=0,
    stop=9223372036854775807
</details>)
```
> Return first index of value.
> 
> Raises ValueError if the value is not present.

## insert(...*3)
```python
staticmethod insert(<details><summary>...</summary>
    self, index, object
</details>)
```
> Insert object before index.

## itell(...*3)
```python
classmethod itell(<details><summary>...</summary>
    user: User, args, kwargs
</details>)
```
> Convenience method for `user.tell(RS.TR().text(*args, **kwargs))`

## join(...*2)
```python
staticmethod join(<details><summary>...</summary>
    self, tellraws: tuple
</details>) -> Self
```
> <no doc>

## line_break(...*2)
```python
staticmethod line_break(<details><summary>...</summary>
    self, count: int = 1
</details>)
```
> Append n newlines to self (where n >= 0)

## pop(...*2)
```python
staticmethod pop(<details><summary>...</summary>
    self, index=-1
</details>)
```
> Remove and return item at index (default last).
> 
> Raises IndexError if list is empty or index is out of range.

## remove(...*2)
```python
staticmethod remove(<details><summary>...</summary>
    self, value
</details>)
```
> Remove first occurrence of value.
> 
> Raises ValueError if the value is not present.

## render(...*1)
```python
staticmethod render(self)
```
> <no doc>

## reverse(...*1)
```python
staticmethod reverse(self)
```
> Reverse *IN PLACE*.

## sort(...*3)
```python
staticmethod sort(<details><summary>...</summary>
    self, key=None, reverse=False
</details>)
```
> Sort the list in ascending order and return None.
> 
> The sort is in-place (i.e. the list itself is modified) and stable (i.e. the
> order of two equal elements is maintained).
> 
> If a key function is given, apply it once to each list item and sort them,
> ascending or descending, according to their function values.
> 
> The reverse flag can be set to sort in descending order.

## text(...*11)
```python
staticmethod text(<details><summary>...</summary>
    self, text: str, color: str | None = None,
    fmt: _rsruntime.lib.rs_userio.TextFormat | dict = 0, insertion: str | None = None, type: TextType = TextType.TEXT,
    objective: None | str = None, click_event: _rsruntime.lib.rs_userio.ClickEvent | None = None, click_contents: None | str = None,
    hover_event: _rsruntime.lib.rs_userio.HoverEvent | None = None, hover_contents: Union = None
</details>)
```
> Appends a tellraw text to self
>     text is the text to show unless type is:
>         SELECTOR, in which case text is the selector type
>         SCORE, in which case text is the name of the player
>         KEYBIND, in which case text is the ID of the keybind
>     fmt is the formatting to apply to the text
>     insertion is text that is entered into the user's chat-box when the text is shift-clicked
>     type should be self-explanatory
>     objective is None unless type is SCORE, in which case objective is the scoreboard objective
>     click_event is either a ClickEvent or None for nothing
>         click_contents is the text to use for the click_event (the URL to open, text to copy, etc.)
>     hover_event is either a HoverEvent or None for nothing
>         hover_contents is the data to use for the hover_event (the entity to display, the TellRaw to show [as text])
# `ChatCommands` (shorthand: `RSCC`)

## compose_command(...*2)
```python
method compose_command(<details><summary>...</summary>
    cmd: str, args: str | None
</details>) -> str
```
> Compiles cmd and args together using various configuration to compose a command string

## help(...*4)
```python
method help(<details><summary>...</summary>
    user: User, on: Union = None, section: None | str = None,
    force_console: bool | None = None
</details>)
```
> Shows help on commands or sections.
>     If on is "section", then shows help on the section specified by "section"
>     If on is a command, then shows help on that command
>     If on is not supplied, then shows a list of top-level sections

## helpcmd_for(...*2)
```python
method helpcmd_for(<details><summary>...</summary>
    item: str | None = None, for_section: bool = False
</details>)
```
> Composes a help command for the item

## parse_command(...*1)
```python
method parse_command(line: str) -> tuple
```
> Returns:
>   - a (True, ChatCommand, args) tuple if the line is a ChatCommand
>   - a (False, command, args) tuple if the line matches as a ChatCommand, but the command in question hasn't been registered
>   - None if the line doesn't match as a ChatCommand

## register(...*2)
```python
method register(<details><summary>...</summary>
    cmd: ChatCommands.ChatCommand, aliases: set = set()
</details>) -> ChatCommands.ChatCommand
```
> <no doc>

## register_func(...*4)
```python
method register_func(<details><summary>...</summary>
    func: Callable, aliases: set = set(), permission: Perm = 80,
    help_section: str | tuple[str, ...] = ()
</details>) -> ChatCommands.ChatCommand
```
> <no doc>

## run_command(...*3)
```python
method run_command(<details><summary>...</summary>
    user: User, line: str, not_secure: bool = False
</details>)
```
> <no doc>
# `Convenience` (shorthand: `RS_`)

## command(...*1)
```python
staticmethod command(command: str) -> None | typing.Any
```
> Writes a command to the server
>     Equivelant to RS.SM.write(line)

## inject_line(...*1)
```python
staticmethod inject_line(line: str)
```
> Injects a line into LineParser, as if it was read from the ServerManager
>     Equivelant to RS.LP.handle_line(line)

## listen_chat(...*1)
```python
staticmethod listen_chat(callback: Callable)
```
> Registers a callback for when LineParser reads a chat message
>     The callback should have three arguments:
>     - the user (RS.UM.User object)
>     - the line (str)
>     - if the message was "not secure" (bool)

## say(...*1)
```python
staticmethod say(text: str)
```
> <no doc>

## tell(...*2)
```python
staticmethod tell(<details><summary>...</summary>
    user: _rsruntime.lib.rs_usermgr.UserManager.User | str, text: str
</details>)
```
> <no doc>

## tellraw(...*12)
```python
staticmethod tellraw(<details><summary>...</summary>
    name: str, old_name: str | None = None, uuid: str | object | None = None,
    connected: bool = False, ip: str | None = None, port: int | None = None,
    origin: str | None = None, entity_id: int | None = None, login_coords: tuple[float] | None = None,
    last_connected: time.struct_time | None = None, last_disconnected: time.struct_time | None = None, _no_cache: bool = False
</details>) -> None
```
> Tells a user something. See RS.TR.text for more advanced usage
>     This function uses RS.TR.itell
