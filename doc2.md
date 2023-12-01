# `RunServer` (imported as `RS`)
> None
# `Bootstrapper` (`RS.BS`)

## access_entrypoint(...)
`def access_entrypoint(ep: str)`` -> types.ModuleType`
> Loads the entrypoint's surrounding module

## bootstrap(...)
`def bootstrap(close_after: bool = True)`
> Executes the base manifest, then accesses, assigns, and chainloads the entrypoint

## chainload_entrypoint(...)
`def chainload_entrypoint(rs: Callable)`
> Runs the entrypoint's __call__ method

## close(...)
`def close(do_exit: bool | int = False)`
> Executes all shutdown callbacks and closes logging (logging.shutdown()), and exits with exit code do_exit if it isn't False

## ensure_python_version()
`@classmethod
def ensure_python_version()`
> Ensure that the Python version meets the minimum requirements

## parse_arguments(...)
`def parse_arguments(args=None)`
> Generate and ArgumentParser and parse (known) arguments

## register_onclose(...)
`def register_onclose(cb: Callable)`
> Registers a function to run when self.close() is called

## run_base_manifest()
`def run_base_manifest()`
> Executes the base manifest (_rsruntime/MANIFEST.ini)

## setup_logger()
`def setup_logger()`` -> logging.Logger`
> Sets up self.logger, as well as logging.INFOPLUS/IRRECOVERABLE and Logger.infop/irrec()

## stage_entrypoint(...)
`def stage_entrypoint(rs_outer: types.ModuleType)`` -> rs_outer.RunServer`
> Initializes the entrypoint's class (with self as an argument)


# `BetterPPrinter` (`RS.U.BetterPPrinter`)

### format(...)
`@staticmethod
def format(self, obj, _indent_: int = 0)`` -> Generator`
> <no doc>

### formats(...)
`@staticmethod
def formats(self, obj, joiner: str = )`` -> str`
> <no doc>

### writes(...)
`@staticmethod
def writes(...)`
<details><summary>Parameters...</summary>
```python
    self, obj, fp=<_io.TextIOWrapper name='<stdout>' mode='w' encoding='utf-8'>,
    end: str = 
, delay: float | None = None, collect: Union = None
```
</details>
> <no doc>

# `Hooks` (`RS.U.Hooks`)

### register(...)
`@staticmethod
def register(self, hook: HookType, callback: FuncType)`
> Adds a callback to be called by __call__(hook)

### unregister(...)
`@staticmethod
def unregister(self, hook: HookType, callback: FuncType)`
> Removes a callback that would be called by __call__(hook) (if it exists)

### unregister_hook(...)
`@staticmethod
def unregister_hook(self, hook: HookType)`
> Deletes all callbacks that would be called by __call__(hook)

# `INIBackedDict` (`RS.U.INIBackedDict`)

### bettergetter(...)
`@staticmethod
def bettergetter(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, default: Union = Behavior.RAISE,
    set_default: bool = True
```
</details>` -> Union`
> Gets the value of key
>     If the key is missing, then:
>         if default is Behavior.RAISE: raises KeyError
>         otherwise: returns default, and if set_default is truthy then sets the key to default

### contains(...)
`@staticmethod
def contains(self, key: Key, _tree: Optional = None)`` -> bool`
> Returns whether or not the key exists

### get(...)
`@staticmethod
def get(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, default: Union = Behavior.RAISE,
    _tree: Optional = None
```
</details>` -> Deserialized`
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

### get(...)
`@staticmethod
def get(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, default: Union = Behavior.RAISE,
    _tree: Optional = None
```
</details>` -> Deserialized`
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

### is_autosyncing(...)
`@staticmethod
def is_autosyncing(self)`` -> bool`
> Returns whether or not the internal watchdog timer is ticking

### items_full(...)
`@staticmethod
def items_full(self, start_key: Key, key_join: bool = True)`` -> Generator`
> Iterates over every (key, value) pair, yielding the entire key

### items_short(...)
`@staticmethod
def items_short(self, start_key: Key)`
> Iterates over every (key, value) pair, yielding the last part of the key

### key(...)
`@classmethod
def key(key: Key, top_level: bool = False)`` -> tuple`
> Transform a string / tuple of strings into a key

### keys(...)
`@staticmethod
def keys(self, start_key: Key | None = None, key_join: bool = True)`` -> Generator`
> Iterates over every key

### path_from_topkey(...)
`@staticmethod
def path_from_topkey(self, topkey: str)`
> Returns the Path corresponding to the top-key's file

### readin(...)
`@staticmethod
def readin(self, topkey: str)`
> Reads in a top-level key

### readin_modified(...)
`@staticmethod
def readin_modified(self)`
> Reads in top-level keys that have been changed

### setitem(...)
`@staticmethod
def setitem(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, val: Serializable,
    _tree: Optional = None
```
</details>
> Sets a key to a value

### sort(...)
`@staticmethod
def sort(self, by: Callable = <lambda>)`
> Sorts the data of this INIBackedDict in-place, marking all touched sections as dirty

### start_autosync(...)
`@staticmethod
def start_autosync(self)`
> Starts the internal watchdog timer

### stop_autosync(...)
`@staticmethod
def stop_autosync(self)`
> Stops the internal watchdog timer

### sync(...)
`@staticmethod
def sync(self)`
> Convenience method for writeback_dirty and readin_modified

### values(...)
`@staticmethod
def values(self, start_key: Key)`` -> Generator`
> Iterates over every value

### writeback(...)
`@staticmethod
def writeback(...)`
<details><summary>Parameters...</summary>
```python
    self, topkey: str, only_if_dirty: bool = True,
    clean: bool = True
```
</details>
> Writes back a top-level key

### writeback_dirty(...)
`@staticmethod
def writeback_dirty(self)`
> <no doc>

# `JSONBackedDict` (`RS.U.JSONBackedDict`)

### bettergetter(...)
`@staticmethod
def bettergetter(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, default: Union = Behavior.RAISE,
    set_default: bool = True
```
</details>` -> Union`
> Gets the value of key
>     If the key is missing, then:
>         if default is Behavior.RAISE: raises KeyError
>         otherwise: returns default, and if set_default is truthy then sets the key to default

### contains(...)
`@staticmethod
def contains(self, key: Key, _tree: Optional = None)`` -> bool`
> Returns whether or not the key exists

### get(...)
`@staticmethod
def get(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, default: Union = Behavior.RAISE,
    _tree: Optional = None
```
</details>` -> Deserialized`
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

### get(...)
`@staticmethod
def get(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, default: Union = Behavior.RAISE,
    _tree: Optional = None
```
</details>` -> Deserialized`
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

### is_autosyncing(...)
`@staticmethod
def is_autosyncing(self)`` -> bool`
> Returns whether or not the internal watchdog timer is ticking

### items_full(...)
`@staticmethod
def items_full(self, start_key: Key, key_join: bool = True)`` -> Generator`
> Iterates over every (key, value) pair, yielding the entire key

### items_short(...)
`@staticmethod
def items_short(self, start_key: Key)`
> Iterates over every (key, value) pair, yielding the last part of the key

### key(...)
`@classmethod
def key(key: Key, top_level: bool = False)`` -> tuple`
> Transform a string / tuple of strings into a key

### keys(...)
`@staticmethod
def keys(self, start_key: Key | None = None, key_join: bool = True)`` -> Generator`
> Iterates over every key

### path_from_topkey(...)
`@staticmethod
def path_from_topkey(self, topkey: str)`
> Returns the Path corresponding to the top-key's file

### readin(...)
`@staticmethod
def readin(self, topkey: str)`
> Reads in a top-level key

### readin_modified(...)
`@staticmethod
def readin_modified(self)`
> Reads in top-level keys that have been changed

### setitem(...)
`@staticmethod
def setitem(...)`
<details><summary>Parameters...</summary>
```python
    self, key: Key, val: Serializable,
    _tree: Optional = None
```
</details>
> Sets a key to a value

### sort(...)
`@staticmethod
def sort(self, by: Callable = <lambda>)`
> Sorts the data of this JSONBackedDict (semi-)in-place, marking all touched sections as dirty

### start_autosync(...)
`@staticmethod
def start_autosync(self)`
> Starts the internal watchdog timer

### stop_autosync(...)
`@staticmethod
def stop_autosync(self)`
> Stops the internal watchdog timer

### sync(...)
`@staticmethod
def sync(self)`
> Convenience method for writeback_dirty and readin_modified

### values(...)
`@staticmethod
def values(self, start_key: Key)`` -> Generator`
> Iterates over every value

### writeback(...)
`@staticmethod
def writeback(...)`
<details><summary>Parameters...</summary>
```python
    self, topkey: str, only_if_dirty: bool = True,
    clean: bool = True
```
</details>
> Writes back a top-level key

### writeback_dirty(...)
`@staticmethod
def writeback_dirty(self)`
> <no doc>

# `Util` (`RS.U`)


# `Flags` (`RS.F`)


# `Config` (`RS.C`)

## bettergetter(...)
`def bettergetter(key: Key, default: Union = Behavior.RAISE, set_default: bool = True)`` -> Union`
> Gets the value of key
>     If the key is missing, then:
>         if default is Behavior.RAISE: raises KeyError
>         otherwise: returns default, and if set_default is truthy then sets the key to default

## close()
`def close()`
> <no doc>

## contains(...)
`def contains(key: Key, _tree: Optional = None)`` -> bool`
> Returns whether or not the key exists

## get(...)
`def get(key: Key, default: Union = Behavior.RAISE, _tree: Optional = None)`` -> Deserialized`
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

## get(...)
`def get(key: Key, default: Union = Behavior.RAISE, _tree: Optional = None)`` -> Deserialized`
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

## is_autosyncing()
`def is_autosyncing()`` -> bool`
> Returns whether or not the internal watchdog timer is ticking

## items_full(...)
`def items_full(start_key: Key, key_join: bool = True)`` -> Generator`
> Iterates over every (key, value) pair, yielding the entire key

## items_short(...)
`def items_short(start_key: Key)`
> Iterates over every (key, value) pair, yielding the last part of the key

## key(...)
`@classmethod
def key(key: Key, top_level: bool = False)`` -> tuple`
> Transform a string / tuple of strings into a key

## keys(...)
`def keys(start_key: Key | None = None, key_join: bool = True)`` -> Generator`
> Iterates over every key

## mass_set_default(...)
`def mass_set_default(pfx: str | None = None, dict_vals: dict[str, Serializable] | None = None, values: Serializable)`
> Sets a large amount of default values
>     When pfx is not None, it is prepended (with a / if it doesn't already have one) to each key
> Values are either given through dict_vals or **values (keyword args)
>     Using both is probably bad but not prohibited
>         A SyntaxWarning shall be issued upon you to remind you of your choices.
>     If a value is in both and is not the same, a ValueError is raised
>         Once this has been checked, they are merged together
> If a total of 0 values are given, an error is logged
> Otherwise, an info is logged decribing how many keys will be set

## path_from_topkey(...)
`def path_from_topkey(topkey: str)`
> Returns the Path corresponding to the top-key's file

## readin(...)
`def readin(topkey: str)`
> Reads in a top-level key

## readin_modified()
`def readin_modified()`
> Reads in top-level keys that have been changed

## set_default(...)
`def set_default(option: str | tuple[str], value: Serializable)`
> Sets an option if it does not exist

## setitem(...)
`def setitem(key: Key, val: Serializable, _tree: Optional = None)`
> Sets a key to a value

## sort(...)
`def sort(by: Callable = <lambda>)`
> Sorts the data of this INIBackedDict in-place, marking all touched sections as dirty

## start_autosync()
`def start_autosync()`
> Starts the internal watchdog timer

## stop_autosync()
`def stop_autosync()`
> Stops the internal watchdog timer

## sync()
`def sync()`
> Convenience method for writeback_dirty and readin_modified

## values(...)
`def values(start_key: Key)`` -> Generator`
> Iterates over every value

## writeback(...)
`def writeback(topkey: str, only_if_dirty: bool = True, clean: bool = True)`
> Writes back a top-level key

## writeback_dirty()
`def writeback_dirty()`
> <no doc>


# `ExceptionHandlers` (`RS.EH`)

## hookin()
`def hookin()`
> <no doc>

## hookout()
`def hookout()`
> <no doc>

## register_exception_hook(...)
`def register_exception_hook(callback: Callable)`
> <no doc>

## register_thread_exception_hook(...)
`def register_thread_exception_hook(callback: Callable)`
> <no doc>

## register_unraisable_hook(...)
`def register_unraisable_hook(callback: Callable)`
> <no doc>


# `MCLang` (`RS.L`)

## extract_lang()
`def extract_lang()`` -> dict`
> Extracts the language file from a server JAR file, sets and returns self.lang

## lang_to_pattern(...)
`def lang_to_pattern(lang: str, group_names: tuple[str, ...] | None = None, prefix_suffix: str = ^{}$)`` -> Pattern`
> <no doc>

## strip_prefix(...)
`def strip_prefix(line: str)`` -> tuple`
> <no doc>


# `LineParser` (`RS.LP`)

## handle_line(...)
`def handle_line(line: str)`
> <no doc>

## register_callback(...)
`def register_callback(patt: Pattern, callback: Union, with_prefix: bool = True)`
> Registers a callback
>     If keep_prefix, then lines that have the prefix are passed. callback should have the signature: `callback(match: re.Match, prefix: re.Match, t: time.struct_time)`
>     Otherwise, lines that don't have a prefix are passed; the callback should have the signature: `callback(match: re.Match)`

## register_chat_callback(...)
`def register_chat_callback(callback: Callable)`
> Registers a callback for when chat is recieved
>     The callback should have the signature `callback(user: RS.UserManager.User, message: str, insecure: bool)`


# `PluginManager` (`RS.PM`)

## early_load_plugins()
`def early_load_plugins()`
> <no doc>

## load_plugins()
`def load_plugins()`
> <no doc>

## restart()
`def restart()`
> <no doc>

## start()
`def start()`
> <no doc>


# `ServerManager` (`RS.SM`)

## preferred_order()
`@classmethod
def preferred_order()`` -> list`
> <no doc>

## register(...)
`@classmethod
def register(manager_type: Type)`
> <no doc>


# `UserManager` (`RS.UM`)

## close()
`def close()`
> <no doc>


# `TellRaw` (`RS.TR`)

## append(...)
`@staticmethod
def append(self, object)`
> Append object to the end of the list.

## clear(...)
`@staticmethod
def clear(self)`
> Remove all items from list.

## copy(...)
`@staticmethod
def copy(self)`
> Return a shallow copy of the list.

## count(...)
`@staticmethod
def count(self, value)`
> Return number of occurrences of value.

## extend(...)
`@staticmethod
def extend(self, iterable)`
> Extend list by appending elements from the iterable.

## ijoin(...)
`@staticmethod
def ijoin(self, tellraws: tuple)`` -> Generator`
> <no doc>

## index(...)
`@staticmethod
def index(...)`
<details><summary>Parameters...</summary>
```python
    self, value, start=0,
    stop=9223372036854775807
```
</details>
> Return first index of value.
> 
> Raises ValueError if the value is not present.

## insert(...)
`@staticmethod
def insert(self, index, object)`
> Insert object before index.

## itell(...)
`@classmethod
def itell(user: User, args, kwargs)`
> Convenience method for `user.tell(RS.TR().text(*args, **kwargs))`

## join(...)
`@staticmethod
def join(self, tellraws: tuple)`` -> Self`
> <no doc>

## line_break(...)
`@staticmethod
def line_break(self, count: int = 1)`
> Append n newlines to self (where n >= 0)

## pop(...)
`@staticmethod
def pop(self, index=-1)`
> Remove and return item at index (default last).
> 
> Raises IndexError if list is empty or index is out of range.

## remove(...)
`@staticmethod
def remove(self, value)`
> Remove first occurrence of value.
> 
> Raises ValueError if the value is not present.

## render(...)
`@staticmethod
def render(self)`
> <no doc>

## reverse(...)
`@staticmethod
def reverse(self)`
> Reverse *IN PLACE*.

## sort(...)
`@staticmethod
def sort(self, key=None, reverse=False)`
> Sort the list in ascending order and return None.
> 
> The sort is in-place (i.e. the list itself is modified) and stable (i.e. the
> order of two equal elements is maintained).
> 
> If a key function is given, apply it once to each list item and sort them,
> ascending or descending, according to their function values.
> 
> The reverse flag can be set to sort in descending order.

## text(...)
`@staticmethod
def text(...)`
<details><summary>Parameters...</summary>
```python
    self, text: str, color: str | None = None,
    fmt: _rsruntime.lib.rs_userio.TextFormat | dict = 0, insertion: str | None = None, type: TextType = TextType.TEXT,
    objective: None | str = None, click_event: _rsruntime.lib.rs_userio.ClickEvent | None = None, click_contents: None | str = None,
    hover_event: _rsruntime.lib.rs_userio.HoverEvent | None = None, hover_contents: Union = None
```
</details>
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


# `ChatCommands` (`RS.CC`)

## compose_command(...)
`def compose_command(cmd: str, args: str | None)`` -> str`
> Compiles cmd and args together using various configuration to compose a command string

## help(...)
`def help(...)`
<details><summary>Parameters...</summary>
```python
    user: User, on: Union = None, section: None | str = None,
    force_console: bool | None = None
```
</details>
> Shows help on commands or sections.
>     If on is "section", then shows help on the section specified by "section"
>     If on is a command, then shows help on that command
>     If on is not supplied, then shows a list of top-level sections

## helpcmd_for(...)
`def helpcmd_for(item: str | None = None, for_section: bool = False)`
> Composes a help command for the item

## parse_command(...)
`def parse_command(line: str)`` -> tuple`
> Returns:
>   - a (True, ChatCommand, args) tuple if the line is a ChatCommand
>   - a (False, command, args) tuple if the line matches as a ChatCommand, but the command in question hasn't been registered
>   - None if the line doesn't match as a ChatCommand

## register(...)
`def register(cmd: ChatCommands.ChatCommand, aliases: set = set())`` -> ChatCommands.ChatCommand`
> <no doc>

## register_func(...)
`def register_func(...)`
<details><summary>Parameters...</summary>
```python
    func: Callable, aliases: set = set(), permission: Perm = 80,
    help_section: str | tuple[str, ...] = ()
```
</details>` -> ChatCommands.ChatCommand`
> <no doc>

## run_command(...)
`def run_command(user: User, line: str, not_secure: bool = False)`
> <no doc>


# `Convenience` (`RS._`)

## command(...)
`@staticmethod
def command(command: str)`` -> None | typing.Any`
> Writes a command to the server
>     Equivelant to RS.SM.write(line)

## inject_line(...)
`@staticmethod
def inject_line(line: str)`
> Injects a line into LineParser, as if it was read from the ServerManager
>     Equivelant to RS.LP.handle_line(line)

## listen_chat(...)
`@staticmethod
def listen_chat(callback: Callable)`
> Registers a callback for when LineParser reads a chat message
>     The callback should have three arguments:
>     - the user (RS.UM.User object)
>     - the line (str)
>     - if the message was "not secure" (bool)

## say(...)
`@staticmethod
def say(text: str)`
> <no doc>

## tell(...)
`@staticmethod
def tell(user: _rsruntime.lib.rs_usermgr.UserManager.User | str, text: str)`
> <no doc>

## tellraw(...)
`@staticmethod
def tellraw(...)`
<details><summary>Parameters...</summary>
```python
    name: str, old_name: str | None = None, uuid: str | object | None = None,
    connected: bool = False, ip: str | None = None, port: int | None = None,
    origin: str | None = None, entity_id: int | None = None, login_coords: tuple[float] | None = None,
    last_connected: time.struct_time | None = None, last_disconnected: time.struct_time | None = None, _no_cache: bool = False
```
</details>` -> None`
> Tells a user something. See RS.TR.text for more advanced usage
>     This function uses RS.TR.itell
