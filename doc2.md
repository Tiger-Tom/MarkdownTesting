*This documentation was generated with `devel/makedoc.py`*
> Documentation is generated from the source code.
> Documentation is quite probably incomplete or inaccurate, just look at this script!

# `RunServer` (imported as `RS`)
> <no doc>

# `Bootstrapper` (`RS.BS`)
[`_rsruntime/rs_BOOTSTRAP.py`](/_rsruntime/rs_BOOTSTRAP.py "Source")
[Standalone doc: parts/RS/Bootstrapper.md](./parts/RS/Bootstrapper.md)
> Does the necessary startup and take-down for RunServer

## access_entrypoint(...)
```python
def access_entrypoint(ep: str) -> types.ModuleType
```
[`_rsruntime/rs_BOOTSTRAP.py@207:211`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L207)  
> Loads the entrypoint's surrounding module

## bootstrap(...)
```python
def bootstrap(close_after: bool = True)
```
[`_rsruntime/rs_BOOTSTRAP.py@180:193`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L180)  
> Executes the base manifest, then accesses, assigns, and chainloads the entrypoint

## chainload_entrypoint(...)
```python
def chainload_entrypoint(rs: Callable)
```
[`_rsruntime/rs_BOOTSTRAP.py@216:220`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L216)  
> Runs the entrypoint's __call__ method

## close(...)
```python
def close(do_exit: bool | int = False)
```
[`_rsruntime/rs_BOOTSTRAP.py@224:232`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L224)  
> Executes all shutdown callbacks and closes logging (logging.shutdown()), and exits with exit code do_exit if it isn't False

## ensure_python_version()
```python
@classmethod
def ensure_python_version()
```
[`_rsruntime/rs_BOOTSTRAP.py@69:73`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L69)  
> Ensure that the Python version meets the minimum requirements

## parse_arguments(...)
```python
def parse_arguments(args=None)
```
[`_rsruntime/rs_BOOTSTRAP.py@75:91`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L75)  
> Generate and ArgumentParser and parse (known) arguments

## register_onclose(...)
```python
def register_onclose(cb: Callable)
```
[`_rsruntime/rs_BOOTSTRAP.py@233:235`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L233)  
> Registers a function to run when self.close() is called

## run_base_manifest()
```python
def run_base_manifest()
```
[`_rsruntime/rs_BOOTSTRAP.py@195:205`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L195)  
> Executes the base manifest (_rsruntime/MANIFEST.ini)

## setup_logger()
```python
def setup_logger() -> logging.Logger
```
[`_rsruntime/rs_BOOTSTRAP.py@93:176`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L93)  
> Sets up self.logger, as well as logging.INFOPLUS/IRRECOVERABLE and Logger.infop/irrec()

## stage_entrypoint(...)
```python
def stage_entrypoint(rs_outer: types.ModuleType) -> rs_outer.RunServer
```
[`_rsruntime/rs_BOOTSTRAP.py@212:215`](/_rsruntime/rs_BOOTSTRAP.py?plain=1#L212)  
> Initializes the entrypoint's class (with self as an argument)
**[Standalone: parts/RS/Bootstrapper.md](./parts/RS/Bootstrapper.md)**


# `Flags` (`RS.F`)
[Standalone doc: parts/RS/Flags.md](./parts/RS/Flags.md)
> A simple attribute-based namespace.
> 
> SimpleNamespace(**kwargs)
> Initialize self.  See help(type(self)) for accurate signature.
**[Standalone: parts/RS/Flags.md](./parts/RS/Flags.md)**


# `Config` (`RS.C`)
[`_rsruntime/lib/rs_config.py`](/_rsruntime/lib/rs_config.py "Source")
[Standalone doc: parts/RS/Config.md](./parts/RS/Config.md)
> A thin wrapper around INIBackedDict

## bettergetter(...)
```python
def bettergetter(key: Key, default: ForwardRef('FileBackedDict.Behavior.RAISE') | Any = Behavior.RAISE, set_default: bool = True) -> Deserialized | Any
```
[`_rsruntime/util/fbd.py@137:153`](/_rsruntime/util/fbd.py?plain=1#L137)  
> Gets the value of key
>     If the key is missing, then:
>         if default is Behavior.RAISE: raises KeyError
>         otherwise: returns default, and if set_default is truthy then sets the key to default

## close()
```python
def close()
```
[`_rsruntime/lib/rs_config.py@65:68`](/_rsruntime/lib/rs_config.py?plain=1#L65)  
> <no doc>

## contains(...)
```python
def contains(key: Key, _tree: MutableMapping | NoneType = None) -> bool
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Returns whether or not the key exists

## get(...)
```python
def get(key: Key, default: ForwardRef('FileBackedDict.Behavior.RAISE') | Serializable = Behavior.RAISE, _tree: MutableMapping | NoneType = None) -> Deserialized
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

## get(...)
```python
def get(key: Key, default: ForwardRef('FileBackedDict.Behavior.RAISE') | Serializable = Behavior.RAISE, _tree: MutableMapping | NoneType = None) -> Deserialized
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Gets the value of key
>     If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

## is_autosyncing()
```python
def is_autosyncing() -> bool
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Returns whether or not the internal watchdog timer is ticking

## items_full(...)
```python
def items_full(start_key: Key, key_join: bool = True) -> Generator
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Iterates over every (key, value) pair, yielding the entire key

## items_short(...)
```python
def items_short(start_key: Key)
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Iterates over every (key, value) pair, yielding the last part of the key

## key(...)
```python
@classmethod
def key(key: Key, top_level: bool = False) -> tuple
```
[`_rsruntime/util/fbd.py@65:78`](/_rsruntime/util/fbd.py?plain=1#L65)  
> Transform a string / tuple of strings into a key

## keys(...)
```python
def keys(start_key: Key | None = None, key_join: bool = True) -> Generator
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Iterates over every key

## mass_set_default(...)
```python
def mass_set_default(pfx: str | None = None, dict_vals: dict[str, Serializable] | None = None, values: Serializable)
```
[`_rsruntime/lib/rs_config.py@28:64`](/_rsruntime/lib/rs_config.py?plain=1#L28)  
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
```python
def path_from_topkey(topkey: str)
```
[`_rsruntime/util/fbd.py@79:81`](/_rsruntime/util/fbd.py?plain=1#L79)  
> Returns the Path corresponding to the top-key's file

## readin(...)
```python
def readin(topkey: str)
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Reads in a top-level key

## readin_modified()
```python
def readin_modified()
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Reads in top-level keys that have been changed

## set_default(...)
```python
def set_default(option: str | tuple[str], value: Serializable)
```
[`_rsruntime/lib/rs_config.py@24:27`](/_rsruntime/lib/rs_config.py?plain=1#L24)  
> Sets an option if it does not exist

## setitem(...)
```python
def setitem(key: Key, val: Serializable, _tree: MutableMapping | NoneType = None)
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Sets a key to a value

## sort(...)
```python
def sort(by: Callable = <lambda>)
```
[`_rsruntime/util/fbd.py@277:283`](/_rsruntime/util/fbd.py?plain=1#L277)  
> Sorts the data of this INIBackedDict in-place, marking all touched sections as dirty

## start_autosync()
```python
def start_autosync()
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Starts the internal watchdog timer

## stop_autosync()
```python
def stop_autosync()
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Stops the internal watchdog timer

## sync()
```python
def sync()
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Convenience method for writeback_dirty and readin_modified

## values(...)
```python
def values(start_key: Key) -> Generator
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Iterates over every value

## writeback(...)
```python
def writeback(topkey: str, only_if_dirty: bool = True, clean: bool = True)
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> Writes back a top-level key

## writeback_dirty()
```python
def writeback_dirty()
```
[`_rsruntime/util/locked_resource.py@88:91`](/_rsruntime/util/locked_resource.py?plain=1#L88)  
> <no doc>
**[Standalone: parts/RS/Config.md](./parts/RS/Config.md)**


# `ExceptionHandlers` (`RS.EH`)
[`_rsruntime/lib/rs_exceptionhandlers.py`](/_rsruntime/lib/rs_exceptionhandlers.py "Source")
[Standalone doc: parts/RS/ExceptionHandlers.md](./parts/RS/ExceptionHandlers.md)

## hookin()
```python
def hookin()
```
[`_rsruntime/lib/rs_exceptionhandlers.py@38:41`](/_rsruntime/lib/rs_exceptionhandlers.py?plain=1#L38)  
> <no doc>

## hookout()
```python
def hookout()
```
[`_rsruntime/lib/rs_exceptionhandlers.py@46:49`](/_rsruntime/lib/rs_exceptionhandlers.py?plain=1#L46)  
> <no doc>

## register_exception_hook(...)
```python
def register_exception_hook(callback: Callable)
```
[`_rsruntime/lib/rs_exceptionhandlers.py@54:55`](/_rsruntime/lib/rs_exceptionhandlers.py?plain=1#L54)  
> <no doc>

## register_thread_exception_hook(...)
```python
def register_thread_exception_hook(callback: Callable)
```
[`_rsruntime/lib/rs_exceptionhandlers.py@58:59`](/_rsruntime/lib/rs_exceptionhandlers.py?plain=1#L58)  
> <no doc>

## register_unraisable_hook(...)
```python
def register_unraisable_hook(callback: Callable)
```
[`_rsruntime/lib/rs_exceptionhandlers.py@56:57`](/_rsruntime/lib/rs_exceptionhandlers.py?plain=1#L56)  
> <no doc>
**[Standalone: parts/RS/ExceptionHandlers.md](./parts/RS/ExceptionHandlers.md)**


# `MCLang` (`RS.L`)
[`_rsruntime/lib/rs_lineparser.py`](/_rsruntime/lib/rs_lineparser.py "Source")
[Standalone doc: parts/RS/MCLang.md](./parts/RS/MCLang.md)

## extract_lang()
```python
def extract_lang() -> dict
```
[`_rsruntime/lib/rs_lineparser.py@77:91`](/_rsruntime/lib/rs_lineparser.py?plain=1#L77)  
> Extracts the language file from a server JAR file, sets and returns self.lang

## lang_to_pattern(...)
```python
def lang_to_pattern(lang: str, group_names: tuple[str, ...] | None = None, prefix_suffix: str = ^{}$) -> Pattern
```
[`_rsruntime/lib/rs_lineparser.py@41:75`](/_rsruntime/lib/rs_lineparser.py?plain=1#L41)  
> <no doc>

## strip_prefix(...)
```python
def strip_prefix(line: str) -> tuple
```
[`_rsruntime/lib/rs_lineparser.py@35:39`](/_rsruntime/lib/rs_lineparser.py?plain=1#L35)  
> <no doc>
**[Standalone: parts/RS/MCLang.md](./parts/RS/MCLang.md)**


# `LineParser` (`RS.LP`)
[`_rsruntime/lib/rs_lineparser.py`](/_rsruntime/lib/rs_lineparser.py "Source")
[Standalone doc: parts/RS/LineParser.md](./parts/RS/LineParser.md)

## handle_line(...)
```python
def handle_line(line: str)
```
[`_rsruntime/lib/rs_lineparser.py@115:120`](/_rsruntime/lib/rs_lineparser.py?plain=1#L115)  
> <no doc>

## register_callback(...)
```python
def register_callback(patt: Pattern, callback: Callable | Callable, with_prefix: bool = True)
```
[`_rsruntime/lib/rs_lineparser.py@102:108`](/_rsruntime/lib/rs_lineparser.py?plain=1#L102)  
> Registers a callback
>     If keep_prefix, then lines that have the prefix are passed. callback should have the signature: `callback(match: re.Match, prefix: re.Match, t: time.struct_time)`
>     Otherwise, lines that don't have a prefix are passed; the callback should have the signature: `callback(match: re.Match)`

## register_chat_callback(...)
```python
def register_chat_callback(callback: Callable)
```
[`_rsruntime/lib/rs_lineparser.py@109:114`](/_rsruntime/lib/rs_lineparser.py?plain=1#L109)  
> Registers a callback for when chat is recieved
>     The callback should have the signature `callback(user: RS.UserManager.User, message: str, insecure: bool)`
**[Standalone: parts/RS/LineParser.md](./parts/RS/LineParser.md)**


# `PluginManager` (`RS.PM`)
[`_rsruntime/lib/rs_plugins.py`](/_rsruntime/lib/rs_plugins.py "Source")
[Standalone doc: parts/RS/PluginManager.md](./parts/RS/PluginManager.md)

## early_load_plugins()
```python
def early_load_plugins()
```
[`_rsruntime/lib/rs_plugins.py@171:179`](/_rsruntime/lib/rs_plugins.py?plain=1#L171)  
> <no doc>

## load_plugins()
```python
def load_plugins()
```
[`_rsruntime/lib/rs_plugins.py@181:183`](/_rsruntime/lib/rs_plugins.py?plain=1#L181)  
> <no doc>

## restart()
```python
def restart()
```
[`_rsruntime/lib/rs_plugins.py@212:213`](/_rsruntime/lib/rs_plugins.py?plain=1#L212)  
> <no doc>

## start()
```python
def start()
```
[`_rsruntime/lib/rs_plugins.py@210:211`](/_rsruntime/lib/rs_plugins.py?plain=1#L210)  
> <no doc>
**[Standalone: parts/RS/PluginManager.md](./parts/RS/PluginManager.md)**


# `ServerManager` (`RS.SM`)
[`_rsruntime/lib/rs_servmgr.py`](/_rsruntime/lib/rs_servmgr.py "Source")
[Standalone doc: parts/RS/ServerManager.md](./parts/RS/ServerManager.md)
> Initialize self.  See help(type(self)) for accurate signature.

## preferred_order()
```python
@classmethod
def preferred_order() -> list
```
[`_rsruntime/lib/rs_servmgr.py@199:201`](/_rsruntime/lib/rs_servmgr.py?plain=1#L199)  
> <no doc>

## register(...)
```python
@classmethod
def register(manager_type: Type)
```
[`_rsruntime/lib/rs_servmgr.py@196:198`](/_rsruntime/lib/rs_servmgr.py?plain=1#L196)  
> <no doc>
**[Standalone: parts/RS/ServerManager.md](./parts/RS/ServerManager.md)**


# `UserManager` (`RS.UM`)
[`_rsruntime/lib/rs_usermgr.py`](/_rsruntime/lib/rs_usermgr.py "Source")
[Standalone doc: parts/RS/UserManager.md](./parts/RS/UserManager.md)

## close()
```python
def close()
```
[`_rsruntime/lib/rs_usermgr.py@168:170`](/_rsruntime/lib/rs_usermgr.py?plain=1#L168)  
> <no doc>
**[Standalone: parts/RS/UserManager.md](./parts/RS/UserManager.md)**


# `TellRaw` (`RS.TR`)
[`_rsruntime/lib/rs_userio.py`](/_rsruntime/lib/rs_userio.py "Source")
[Standalone doc: parts/RS/TellRaw.md](./parts/RS/TellRaw.md)
> Generates a TellRaw JSON
>     Praise be to https://www.minecraftjson.com !
> Who doesn't want object-oriented TellRaws???
> Initialize self.  See help(type(self)) for accurate signature.

## append(...)
```python
@staticmethod
def append(self, object)
```
> Append object to the end of the list.

## clear(...)
```python
@staticmethod
def clear(self)
```
> Remove all items from list.

## copy(...)
```python
@staticmethod
def copy(self)
```
> Return a shallow copy of the list.

## count(...)
```python
@staticmethod
def count(self, value)
```
> Return number of occurrences of value.

## extend(...)
```python
@staticmethod
def extend(self, iterable)
```
> Extend list by appending elements from the iterable.

## ijoin(...)
```python
@staticmethod
def ijoin(self, tellraws: tuple) -> Generator
```
[`_rsruntime/lib/rs_userio.py@105:109`](/_rsruntime/lib/rs_userio.py?plain=1#L105)  
> <no doc>

## index(...)
```python
@staticmethod
def index(...)
```
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
```python
@staticmethod
def insert(self, index, object)
```
> Insert object before index.

## itell(...)
```python
@classmethod
def itell(user: User, args, kwargs)
```
[`_rsruntime/lib/rs_userio.py@114:117`](/_rsruntime/lib/rs_userio.py?plain=1#L114)  
> Convenience method for `user.tell(RS.TR().text(*args, **kwargs))`

## join(...)
```python
@staticmethod
def join(self, tellraws: tuple) -> Self
```
[`_rsruntime/lib/rs_userio.py@110:111`](/_rsruntime/lib/rs_userio.py?plain=1#L110)  
> <no doc>

## line_break(...)
```python
@staticmethod
def line_break(self, count: int = 1)
```
[`_rsruntime/lib/rs_userio.py@99:103`](/_rsruntime/lib/rs_userio.py?plain=1#L99)  
> Append n newlines to self (where n >= 0)

## pop(...)
```python
@staticmethod
def pop(self, index=-1)
```
> Remove and return item at index (default last).
> 
> Raises IndexError if list is empty or index is out of range.

## remove(...)
```python
@staticmethod
def remove(self, value)
```
> Remove first occurrence of value.
> 
> Raises ValueError if the value is not present.

## render(...)
```python
@staticmethod
def render(self)
```
[`_rsruntime/lib/rs_userio.py@37:38`](/_rsruntime/lib/rs_userio.py?plain=1#L37)  
> <no doc>

## reverse(...)
```python
@staticmethod
def reverse(self)
```
> Reverse *IN PLACE*.

## sort(...)
```python
@staticmethod
def sort(self, key=None, reverse=False)
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

## text(...)
```python
@staticmethod
def text(...)
```
<details><summary>Parameters...</summary>
```python
    self, text: str, color: str | None = None,
    fmt: _rsruntime.lib.rs_userio.TextFormat | dict = 0, insertion: str | None = None, type: TextType = TextType.TEXT,
    objective: None | str = None, click_event: _rsruntime.lib.rs_userio.ClickEvent | None = None, click_contents: None | str = None,
    hover_event: _rsruntime.lib.rs_userio.HoverEvent | None = None, hover_contents: NoneType | ForwardRef('TellRaw') | tuple | dict = None
```
</details>
[`_rsruntime/lib/rs_userio.py@43:98`](/_rsruntime/lib/rs_userio.py?plain=1#L43)  
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
**[Standalone: parts/RS/TellRaw.md](./parts/RS/TellRaw.md)**


# `ChatCommands` (`RS.CC`)
[`_rsruntime/lib/rs_userio.py`](/_rsruntime/lib/rs_userio.py "Source")
[Standalone doc: parts/RS/ChatCommands.md](./parts/RS/ChatCommands.md)

## compose_command(...)
```python
def compose_command(cmd: str, args: str | None) -> str
```
[`_rsruntime/lib/rs_userio.py@325:330`](/_rsruntime/lib/rs_userio.py?plain=1#L325)  
> Compiles cmd and args together using various configuration to compose a command string

## help(...)
```python
def help(...)
```
<details><summary>Parameters...</summary>
```python
    user: User, on: str | Literal | NoneType = None, section: None | str = None,
    force_console: bool | None = None
```
</details>
[`_rsruntime/lib/rs_userio.py@392:458`](/_rsruntime/lib/rs_userio.py?plain=1#L392)  
> Shows help on commands or sections.
>     If on is "section", then shows help on the section specified by "section"
>     If on is a command, then shows help on that command
>     If on is not supplied, then shows a list of top-level sections

## helpcmd_for(...)
```python
def helpcmd_for(item: str | None = None, for_section: bool = False)
```
[`_rsruntime/lib/rs_userio.py@465:472`](/_rsruntime/lib/rs_userio.py?plain=1#L465)  
> Composes a help command for the item

## parse_command(...)
```python
def parse_command(line: str) -> tuple
```
[`_rsruntime/lib/rs_userio.py@331:341`](/_rsruntime/lib/rs_userio.py?plain=1#L331)  
> Returns:
>   - a (True, ChatCommand, args) tuple if the line is a ChatCommand
>   - a (False, command, args) tuple if the line matches as a ChatCommand, but the command in question hasn't been registered
>   - None if the line doesn't match as a ChatCommand

## register(...)
```python
def register(cmd: ChatCommands.ChatCommand, aliases: set = set()) -> ChatCommands.ChatCommand
```
[`_rsruntime/lib/rs_userio.py@364:382`](/_rsruntime/lib/rs_userio.py?plain=1#L364)  
> <no doc>

## register_func(...)
```python
def register_func(...) -> ChatCommands.ChatCommand
```
<details><summary>Parameters...</summary>
```python
    func: Callable, aliases: set = set(), permission: Perm = 80,
    help_section: str | tuple[str, ...] = ()
```
</details>
[`_rsruntime/lib/rs_userio.py@360:363`](/_rsruntime/lib/rs_userio.py?plain=1#L360)  
> <no doc>

## run_command(...)
```python
def run_command(user: User, line: str, not_secure: bool = False)
```
[`_rsruntime/lib/rs_userio.py@342:358`](/_rsruntime/lib/rs_userio.py?plain=1#L342)  
> <no doc>
**[Standalone: parts/RS/ChatCommands.md](./parts/RS/ChatCommands.md)**
