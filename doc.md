<a id="RS"></a>

# RS

<a id="RS"></a>

# RS

<a id="RS.Bootstrapper"></a>

## Bootstrapper Objects

```python
class Bootstrapper()
```

Does the necessary startup and take-down for RunServer

<a id="RS.Bootstrapper.ensure_python_version"></a>

#### ensure\_python\_version

```python
@classmethod
def ensure_python_version(cls)
```

Ensure that the Python version meets the minimum requirements

<a id="RS.Bootstrapper.parse_arguments"></a>

#### parse\_arguments

```python
def parse_arguments(args=None)
```

Generate and ArgumentParser and parse (known) arguments

<a id="RS.Bootstrapper.setup_logger"></a>

#### setup\_logger

```python
def setup_logger() -> logging.Logger
```

Sets up self.logger, as well as logging.INFOPLUS/IRRECOVERABLE and Logger.infop/irrec()

<a id="RS.Bootstrapper.bootstrap"></a>

#### bootstrap

```python
def bootstrap(close_after: bool = True)
```

Executes the base manifest, then accesses, assigns, and chainloads the entrypoint

<a id="RS.Bootstrapper.run_base_manifest"></a>

#### run\_base\_manifest

```python
def run_base_manifest()
```

Executes the base manifest (_rsruntime/MANIFEST.ini)

<a id="RS.Bootstrapper.access_entrypoint"></a>

#### access\_entrypoint

```python
def access_entrypoint(ep: str) -> types.ModuleType
```

Loads the entrypoint's surrounding module

<a id="RS.Bootstrapper.stage_entrypoint"></a>

#### stage\_entrypoint

```python
def stage_entrypoint(rs_outer: types.ModuleType) -> 'rs_outer.RunServer'
```

Initializes the entrypoint's class (with self as an argument)

<a id="RS.Bootstrapper.chainload_entrypoint"></a>

#### chainload\_entrypoint

```python
def chainload_entrypoint(rs: typing.Callable)
```

Runs the entrypoint's __call__ method

<a id="RS.Bootstrapper.close"></a>

#### close

```python
def close(do_exit: bool | int = False)
```

Executes all shutdown callbacks and closes logging (logging.shutdown()), and exits with exit code do_exit if it isn't False

<a id="RS.Bootstrapper.register_onclose"></a>

#### register\_onclose

```python
def register_onclose(cb: typing.Callable[[], None])
```

Registers a function to run when self.close() is called

<a id="RS.Manifest"></a>

## Manifest Objects

```python
class Manifest(UserDict)
```

<a id="RS.Manifest.__call__"></a>

#### \_\_call\_\_

```python
def __call__(*,
             skip_verify_local: bool = False,
             skip_update: bool = False,
             skip_execute: bool = False,
             ask_download: bool = True,
             ask_execute: bool = True) -> typing.Self
```

Verifies, upgrades, and executes this manifest

<a id="RS.Manifest.upgrade"></a>

#### upgrade

```python
def upgrade(ask: bool = True, override: bool = False)
```

Updates the local manifest, verifying it and notifying the user of modified and stale files

<a id="RS.Manifest.execute"></a>

#### execute

```python
def execute(ask: bool = True, override: bool = False)
```

Executes the manifest, installing new files and replacing files that don't match the stored hashes

<a id="RS.Manifest.__init__"></a>

#### \_\_init\_\_

```python
def __init__()
```

Use from_dict, from_file, or from_remote instead

<a id="RS.Manifest.set_path"></a>

#### set\_path

```python
def set_path(*,
             base: Path | None = None,
             own: Path | None = None) -> typing.Self
```

Sets the manifest's "target" and "own" paths, and returns the Manifest object for chaining

<a id="RS.Manifest.from_dict"></a>

#### from\_dict

```python
@classmethod
def from_dict(cls, d: ManifestDict) -> typing.Self
```

Initializes the UserDict superclass with a new instance of Manifest, setting d as its "data" attribute

<a id="RS.Manifest.from_json"></a>

#### from\_json

```python
@classmethod
def from_json(cls, jsn: str) -> typing.Self
```

Generates a Manifest instance from JSON text (Convenience method for Manifest.from_json(Manifest.dict_from_json_text(...)))

<a id="RS.Manifest.from_ini"></a>

#### from\_ini

```python
@classmethod
def from_ini(cls, ini: str) -> typing.Self
```

Generates a Manifest instance from INI text (Convenience method for Manifest.from_dict(Manifest.dict_from_ini_text(...)))

<a id="RS.Manifest.dict_from_json_text"></a>

#### dict\_from\_json\_text

```python
@staticmethod
def dict_from_json_text(jsn: str) -> ManifestDict
```

Helper method to convert JSON text to a dictionary (current implementation just calls json.loads)

<a id="RS.Manifest.dict_from_ini_text"></a>

#### dict\_from\_ini\_text

```python
@staticmethod
def dict_from_ini_text(ini: str) -> ManifestDict
```

Helper method to convert INI text into a dict (note that interpolation is disabled and keys are case-sensitive)

<a id="RS.Manifest.from_file"></a>

#### from\_file

```python
@classmethod
def from_file(
        cls,
        path: Path,
        path_type: typing.Literal['json', 'ini'] | None = None) -> typing.Self
```

Initializes Manifest from a file.
Can load from the following file types:
    'json': .json files
    'ini': .ini files
If path_type is given, then attempts to load a file of that type
Otherwise, path_type is guessed from path's suffix, using Manifest.suffix_to_type

<a id="RS.Manifest.from_remote"></a>

#### from\_remote

```python
@classmethod
def from_remote(
        cls,
        url: str,
        path_type: typing.Literal['ini', 'json'] | None = None) -> typing.Self
```

Initializes Manifest from a file, has the same path_type properties of from_file

<a id="RS.Manifest.render_json"></a>

#### render\_json

```python
def render_json(to: typing.TextIO | None = None) -> str
```

Render the Manifest dictionary to JSON (if `to` is given, write it to `to` and return the JSON string)

<a id="RS.Manifest.render_ini"></a>

#### render\_ini

```python
def render_ini(to: None | typing.TextIO = None) -> str
```

Render the Manifest dictionary to INI (if `to` is given, write it to `to` and return the INI string)

<a id="RS.Manifest.compile_dict"></a>

#### compile\_dict

```python
@classmethod
def compile_dict(cls, manif: ManifestDict) -> bytes
```

Compiles dictionaries for signing
Keys are compiled in the following order (by default, see COMPILED_KEY_ORDER): 'creation', 'metadata', 'system', 'files'
with each inner value being added to the compiled data as (where, by default, COMPILED_KEY_VALUE_SEP is 255 and COMPILED_ENTRY_SEP is 0):
    _compile_value(outer_key), COMPILED_KEY_VALUE_SEP, _compile_value(inner_key), COMPILED_KEY_VALUE_SEP, _compile_value(value), COMPILED_KEY_VALUE_SEP, COMPILED_ENTRY_SEP

<a id="RS.Manifest.verify"></a>

#### verify

```python
def verify(other: typing.Self | None = None)
```

Verifies either this manifest or another with this manifest's public key

<a id="RS.Manifest._ManifestFactory"></a>

## \_ManifestFactory Objects

```python
class _ManifestFactory()
```

<a id="RS.Manifest._ManifestFactory.field_system_info__none"></a>

#### field\_system\_info\_\_none

less important system info

<a id="RS.Manifest._ManifestFactory.generate_outline"></a>

#### generate\_outline

```python
def generate_outline(*,
                     system_info_level: typing.Literal['full', 'lite',
                                                       'none'] = 'full',
                     name: str,
                     manifest_upstream: str,
                     content_upstream: str,
                     by: str | None,
                     aka: str | None = None,
                     contact: str | None = None,
                     description: str | None = None) -> ManifestDict
```

Creates the '_' and 'files' fields and populates the 'creation', 'metadata', and 'system' fields

<a id="RS.Manifest._ManifestFactory.generate_dict"></a>

#### generate\_dict

```python
def generate_dict(
    path: Path,
    name: str,
    manifest_upstream: str,
    content_upstream: str,
    *,
    by: str | None,
    aka: str | None = None,
    contact: str | None = None,
    description: str | None = None,
    hash_algorithm: typing.Literal[*hashlib.algorithms_available] = 'sha1',
    key: EdPrivK | Path,
    system_info_level: typing.Literal['full', 'lite', 'none'] = 'full'
) -> ManifestDict
```

Generates a manifest-dict from the given attributes

<a id="RS.Manifest._ManifestFactory.__call__"></a>

#### \_\_call\_\_

```python
@functools.wraps(generate_dict,
                 assigned=('__annotations__', '__type_params__'))
def __call__(*args, **kwargs) -> 'Manifest'
```

Convenience wrapper for {self.}Manifest.from_dict(Manifest.ManifestFactory{|self}.generate_dict(...))

<a id="RS"></a>

# RS

<a id="RS"></a>

# RS

<a id="RS.locked_resource"></a>

# RS.locked\_resource

<a id="RS.locked_resource.LockedResource"></a>

## LockedResource Objects

```python
class LockedResource()
```

Adds a "lock" parameter to class instances (and slots!)
This should be used in tandem with the @locked decorator:
    class DemoLocked(LockedResource): # note subclass
        def __init__(self):
            super().__init__() # note super init, needed to setup .lock
            print("initialized!")
        @locked # note decorator
        def test_lock(self):
            print("lock acquired!")

<a id="RS.locked_resource.LockedClass"></a>

#### LockedClass

```python
def LockedClass(lock_class: AbstractContextManager = RLock,
                *,
                I_KNOW_WHAT_IM_DOING: bool = False)
```

Adds a "classlock" class variable
This should be used in tandem with either the @classlocked or @iclasslocked decorators
    see help(classlockd) or help(iclasslocked) for real demo code
Note that, unless you pass I_KNOW_WHAT_IM_DOING=True, lock_class is instantiated immediately in order to check if it is an instance of AbstractContextManager
    This is to try to help emit a warning if LockedClass is used on a user class without being called (@LockedClass instead of @LockedClass())
    The lock_class must be instantiated to check, as threading.RLock and threading.Lock are actually functions
    I_KNOW_WHAT_IM_DOING=True disables both the immediate instantiation of lock_class, the isinstance check, and the warning
lock_class is the type of lock (or really any context manager will do) to use (defaults to RLock)
Short demo code:
    @LockedClass()
    class Locked: ...
or, to use a custom lock:
    @LockedClass(threading.Semaphore)
    class CustomLocked: ...

<a id="RS.locked_resource.locked"></a>

#### locked

```python
def locked(func: typing.Callable)
```

Waits to acquire the method's self's .lock attribute (uses "with")
This should be used in tandem with the LockedResource superclass:
    class DemoLocked(LockedResource): # note subclass
        def __init__(self):
            super().__init__() # note super init, needed to setup .lock
            print("initialized!")
        @locked # note decorator
        def test_lock(self):
            print("lock acquired!")

<a id="RS.locked_resource.classlocked"></a>

#### classlocked

```python
def classlocked(func: typing.Callable)
```

Similar to @locked, but uses cls's .classlock attribute
Does NOT imply classmethod (use @iclasslocked if you want to do that)
Meant to be used with the @LockedClass class decorator:
    @LockedClass
    class DemoLockedClass:
        @classmethod # note: @classmethod BEFORE @classlocked
        @classlocked # could both be replaced by a single @iclasslocked
        def test_lock(cls):
            print("class lock acquired!")
        @classlocked
        def test_lock_2(self):
            print("class lock acquired on non-classmethod!")

<a id="RS.locked_resource.iclasslocked"></a>

#### iclasslocked

```python
def iclasslocked(func: typing.Callable)
```

Is the same as @classlocked (it even calls it), but also wraps the method in classmethod
Meant to be used with @LockedClass:
    @LockedClass()
    class Locked:
        @iclasslocked
        def classlocked_classmethod(cls):
            print("class lock acquired!")

<a id="RS.hooks"></a>

# RS.hooks

<a id="RS.hooks.GenericHooks"></a>

## GenericHooks Objects

```python
class GenericHooks()
```

A generic hooks class
Allows callback functions (of type FuncType) to be registered with a "key" of HookType
Can be called with the key to call all functions registered with it, passing *args and **kwargs

<a id="RS.hooks.GenericHooks.register"></a>

#### register

```python
def register(hook: HookType, callback: FuncType)
```

Adds a callback to be called by __call__(hook)

<a id="RS.hooks.GenericHooks.unregister"></a>

#### unregister

```python
def unregister(hook: HookType, callback: FuncType)
```

Removes a callback that would be called by __call__(hook) (if it exists)

<a id="RS.hooks.GenericHooks.unregister_hook"></a>

#### unregister\_hook

```python
def unregister_hook(hook: HookType)
```

Deletes all callbacks that would be called by __call__(hook)

<a id="RS.hooks.GenericHooks.__call__"></a>

#### \_\_call\_\_

```python
def __call__(hook: HookType, *args, **kwargs)
```

Calls all callbacks that have been registered to be called by __call__(hook)

<a id="RS.hooks.Hooks"></a>

## Hooks Objects

```python
class Hooks(GenericHooks[typing.Hashable, typing.Callable])
```

The most caustic generic hooks class
    Has no difference in behavior from GenericHooks other than typehinting
        basically syntactic sugar for dict[typing.Hashable, typing.Callable]
Also serves as a container for the other types of hooks

<a id="RS.hooks.SingleHook"></a>

## SingleHook Objects

```python
class SingleHook(GenericHooks[None, typing.Callable])
```

A hooks class that has no key

<a id="RS.hooks.SingleHook.register"></a>

#### register

```python
def register(callback: typing.Callable)
```

Adds a callback to be called by __call__()

<a id="RS.hooks.SingleHook.unregister"></a>

#### unregister

```python
def unregister(callback: typing.Callable)
```

Removes a callback that would be called by __call__() (if it exists)

<a id="RS.hooks.SingleHook.__call__"></a>

#### \_\_call\_\_

```python
def __call__(*args, **kwargs)
```

Calls all callbacks that have been registered to be called by __call__()

<a id="RS.hooks.FuncHooks"></a>

## FuncHooks Objects

```python
class FuncHooks()
```

A hooks class that uses functions that take FuncTakes and return FuncReturns as keys
When called with a FuncTakes, each hook is called with the FuncTakes
    If a hook returns a falsey FuncReturns value, then nothing happens
    If a hook returns a truthy FuncReturns value, then each callback registered under that function is called with the FuncReturns value

<a id="RS.hooks.FuncHooks.__call__"></a>

#### \_\_call\_\_

```python
def __call__(inp: FuncTakes, *args, **kwargs)
```

Calls all keys and passes any truthy responses to all callbacks that have been registered to be called by a __call__(...) matching the inp(ut)

<a id="RS.hooks.ReHooks"></a>

## ReHooks Objects

```python
class ReHooks(GenericHooks[re.Pattern, typing.Callable[[re.Match], ...]])
```

A hooks class that matches patterns as keys
When called with a string, all keys are [search|match|fullmatch]ed (decided upon init) against the string
    'search' (the default): calls each callback with the re.Match of the first place where the pattern produces a match
    'match': calls each callback with the re.Match of the beginning of the string that matches the pattern
    'fullmatch': calls each callback with the re.Match of the entire string if it matches the pattern

<a id="RS.hooks.ReHooks.__call__"></a>

#### \_\_call\_\_

```python
def __call__(line: str, *args, **kwargs)
```

Runs a [search|match|fullmatch]es with each key on line, passing re.Match(es) to all callbacks that have been registered to be called by a __call__(...) matching the line

<a id="RS.hooks.SubHooks"></a>

## SubHooks Objects

```python
class SubHooks()
```

A hooks class that has two keys instead of one
Basically syntactic sugar for either of:
- GenericHooks[HookType, GenericHooks[SubHookType, FuncType]]
- dict[HookType, GenericHooks[SubHookType, FuncType]]

<a id="RS.hooks.SubHooks.register"></a>

#### register

```python
def register(hook: HookType, subhook: SubHookType, callback: FuncType)
```

Adds a callback to be called by __call__(hook, subhook)

<a id="RS.hooks.SubHooks.unregister"></a>

#### unregister

```python
def unregister(hook: HookType, subhook: SubHookType, callback: FuncType)
```

Removes a callback that would be called by __call__(hook, subhook)

<a id="RS.hooks.SubHooks.unregister_subhook"></a>

#### unregister\_subhook

```python
def unregister_subhook(hook: HookType, subhook: SubHookType)
```

Removes all callbacks that would be called by __call__(hook, subhook)

<a id="RS.hooks.SubHooks.unregister_hook"></a>

#### unregister\_hook

```python
def unregister_hook(hook: HookType)
```

Removes all callbacks that would be called by __call__(hook, ...) (with ... being anything)

<a id="RS.hooks.SubHooks.__call__"></a>

#### \_\_call\_\_

```python
def __call__(hook: HookType, subhook: SubHookType, *args, **kwargs)
```

Calls all hooks thet have been registered to be called by __call__(hook, subhook)

<a id="RS.cache"></a>

# RS.cache

<a id="RS.perfcounter"></a>

# RS.perfcounter

<a id="RS.perfcounter.PerfCounter"></a>

## PerfCounter Objects

```python
class PerfCounter(float)
```

Provides an object-oriented (because why not) way to use (and format) time.perf_counter

<a id="RS.perfcounter.PerfCounter.__round__"></a>

#### \_\_round\_\_

```python
def __round__() -> float
```

Rounds time.perf_counter()-self; slightly more efficient than builtin round() as we don't need to handle negatives
    Found to be roughly 113.20% faster than (taking 88.34% of the time of) the equivelant usage of builtin over 50000000 tests
        (calculated via: `_benchmark_round(PerfCounter(), n=50000000, notify_every=0.01)`)

<a id="RS.perfcounter.PerfCounter.__int__"></a>

#### \_\_int\_\_

```python
def __int__() -> int
```

Rounds time.perf_counter()-self to an int; more efficient than builtin round() and keeps a bit more precision than builtin int()

<a id="RS.perfcounter.PerfCounter.__repr__"></a>

#### \_\_repr\_\_

```python
def __repr__() -> str
```

Returns a string representing round(self)

<a id="RS.perfcounter.PerfCounter.__str__"></a>

#### \_\_str\_\_

```python
def __str__()
```

Returns a string containing a rounded representation of self appended by self.sec_text[0] if rounded self is "plural" (not one), otherwise self.sec_text[1]

<a id="RS.fbd_OLD"></a>

# RS.fbd\_OLD

<a id="RS.fbd_OLD.FileBackedDict"></a>

## FileBackedDict Objects

```python
class FileBackedDict(UserDict, basic.LockedResource)
```

A dictionary backed by an on-disk JSON file
Asynchronously synchronizes entries with a file on disk when enabled
Detects file changes by checking its modification time
Detects dict changes by adding keys to a "dirty" flag
Sub-dictionaries can be accessed with "/" notation

<a id="RS.fbd_OLD.FileBackedDict.__hash__"></a>

#### \_\_hash\_\_

```python
def __hash__()
```

Exclusively for functools.cache

<a id="RS.fbd_OLD.FileBackedDict.key"></a>

#### key

```python
@functools.cache
def key(key: str | tuple[str],
        *,
        allow_top_lvl_key: bool = False) -> tuple[str]
```

Converts a str a key, ensures that it matches against key_patt_long
    (or key_patt_shrt if allow_top_lvl_key is truthy)
When passed a tuple of str, simply checks if it meets length requirements

<a id="RS.fbd_OLD.FileBackedDict.key_path"></a>

#### key\_path

```python
@functools.cache
def key_path(key: str | tuple[str]) -> Path
```

Converts the key with self.key(), returns the Path corresponding to its JSON file

<a id="RS.fbd_OLD.FileBackedDict._get_"></a>

#### \_get\_

```python
@basic.locked
def _get_(key: tuple[str],
          *,
          make_if_missing: bool = False,
          no_raise: bool = False) -> dict | None
```

Gets the dictionary referenced by the key, useful for mutating

<a id="RS.fbd_OLD.FileBackedDict.get_item"></a>

#### get\_item

```python
@basic.locked
def get_item(
        key: str | tuple[str],
        *,
        unsafe_allow_get_subkey: bool = False) -> typing.Union[*serializable]
```

Gets an item
    (raises TypeError upon trying to return a dict, use unsafe_allow_get_subkey=True to bypass)
If the top-level key cannot be found, but it exists in JSON form, then it is read in
    (if a key is not found, KeyError is raised)

<a id="RS.fbd_OLD.FileBackedDict.get_set_default"></a>

#### get\_set\_default

```python
def get_set_default(key: str | tuple[str],
                    default,
                    *,
                    unsafe_allow_op_subkey: bool = False)
```

Gets an item.
If the item doesn't exist, tries to set "default" as its value and returns default with set_default

<a id="RS.fbd_OLD.FileBackedDict.set_item"></a>

#### set\_item

```python
def set_item(key: str | tuple[str],
             val: typing.Any | dict,
             *,
             unsafe_allow_set_subkey: bool = False,
             unsafe_allow_assign_dict: bool = False)
```

Sets an item.
    Throws TypeError upon trying to overwrite a subkey, pass unsafe_allow_set_subkey=True (also implied by unsafe_allow_set_top_lvl_key=True) to bypass
    Throws TypeError upon trying to assign a dict (AKA subkey) as a value, pass unsafe_allow_assign_dict=True to bypass

<a id="RS.fbd_OLD.FileBackedDict.set_default"></a>

#### set\_default

```python
def set_default(key: str | tuple[str],
                default,
                unsafe_allow_op_subkey: bool = False,
                unsafe_allow_assign_dict: bool = False)
```

If the item corresponding to key doesn't exist, then sets it to default. Has no effect otherwise

<a id="RS.fbd_OLD.FileBackedDict.contains"></a>

#### contains

```python
@basic.locked
def contains(key: str | tuple[str],
             *,
             unsafe_no_error_on_subkey: bool = False) -> bool
```

Checks if the key exists
    If the key resolves to a subkey, then TypeError is raised unless unsafe_no_error_on_subkey is truthy

<a id="RS.fbd_OLD.FileBackedDict.delete"></a>

#### delete

```python
@basic.locked
def delete(key: str | tuple[str], *, unsafe_allow_delete_subkey: bool = False)
```

Deletes an item
Raises TypeError upon trying to delete a suspected subkey (dict), pass unsafe_allow_delete_subkey=True to bypass

<a id="RS.fbd_OLD.FileBackedDict.remove"></a>

#### remove

```python
@basic.locked
def remove(key: str, *, unsafe_I_know_what_I_am_doing: bool = False)
```

Deletes a top level key AND it's corresponding JSON file. Don't call if you don't know what you are doing

<a id="RS.fbd_OLD.FileBackedDict.prune"></a>

#### prune

```python
@basic.locked
def prune(start_key: str | None = None)
```

Recursively removes empty dictionaries, starting with start_key (or from root if start_key is None)

<a id="RS.fbd_OLD.FileBackedDict.__call__"></a>

#### \_\_call\_\_

```python
def __call__(key: str | tuple[str],
             default: None | typing.Any = None,
             on_missing: on_missing = on_missing.
             SET_RETURN_DEFAULT_BUT_ERROR_ON_NONE)
```

Behavior of on_missing when the key isn't found:
    RETURN_DEFAULT: returns the default field
    SET_RETURN_DEFAULT: same as the get_set_default method
    SET_RETURN_DEFAULT_BUT_ERROR_ON_NONE: (the default) same as SET_RETURN_DEFAULT unless default is None, in which case ExceptionGroup(KeyError, TypeError) is raised
    ERROR: raises KeyError

<a id="RS.fbd_OLD.FileBackedDict.readin_data"></a>

#### readin\_data

```python
@basic.locked
def readin_data(key: str)
```

Reads in data from the JSON value corresponding to key (found via self.key_path)

<a id="RS.fbd_OLD.FileBackedDict.readin_watchdog"></a>

#### readin\_watchdog

```python
@basic.locked
def readin_watchdog()
```

Reads in data from files that have been modified since the last read
If a file is missing, it is removed from the watchdog list

<a id="RS.fbd_OLD.FileBackedDict.writeback"></a>

#### writeback

```python
@basic.locked
def writeback(key: str, *, clean: bool = True, force: bool = False) -> bool
```

Writes back a top-level key to its JSON file
    If "force" is not truthy, and the key is not dirty, then nothing is written back and False is returned
    Otherwise:
    - the data is written back
    - watchdog times are updated
    - the key is "cleaned" (removed from dirty) if clean is Truthy
    - True is returned

<a id="RS.fbd_OLD.FileBackedDict.writeback_dirty"></a>

#### writeback\_dirty

```python
@basic.locked
def writeback_dirty()
```

Writes back all dirty keys

<a id="RS.fbd_OLD.FileBackedDict.sync_all"></a>

#### sync\_all

```python
@basic.locked
def sync_all()
```

Basically notifies the user and runs self.writeback_dirty() and then self.readin_watchdog()

<a id="RS.fbd_OLD.FileBackedDict.start_autosync"></a>

#### start\_autosync

```python
@basic.locked
def start_autosync()
```

Starts the internal watchdog timer

<a id="RS.fbd_OLD.FileBackedDict.stop_autosync"></a>

#### stop\_autosync

```python
@basic.locked
def stop_autosync()
```

Stops the internal watchdog timer

<a id="RS.fbd_OLD.FileBackedDict.is_autosyncing"></a>

#### is\_autosyncing

```python
@basic.locked
def is_autosyncing() -> bool
```

Returns whether or not the internal watchdog timer is ticking

<a id="RS.betterprettyprinter"></a>

# RS.betterprettyprinter

<a id="RS.timer"></a>

# RS.timer

<a id="RS.fbd"></a>

# RS.fbd

<a id="RS.fbd.FileBackedDict"></a>

## FileBackedDict Objects

```python
class FileBackedDict(ABC, LockedResource)
```

A dictionary-like class that is backed by an on-disk file
Asynchronously synchronizes entries with a file on disk
Subfields are accessed with `key_sep` (default: "/")

<a id="RS.fbd.FileBackedDict.key"></a>

#### key

```python
@classmethod
def key(cls, key: Key, *, top_level: bool = False) -> tuple[str, ...]
```

Transform a string / tuple of strings into a key

<a id="RS.fbd.FileBackedDict.path_from_topkey"></a>

#### path\_from\_topkey

```python
def path_from_topkey(topkey: str)
```

Returns the Path corresponding to the top-key's file

<a id="RS.fbd.FileBackedDict.sync"></a>

#### sync

```python
@locked
def sync()
```

Convenience method for writeback_dirty and readin_modified

<a id="RS.fbd.FileBackedDict.start_autosync"></a>

#### start\_autosync

```python
@locked
def start_autosync()
```

Starts the internal watchdog timer

<a id="RS.fbd.FileBackedDict.stop_autosync"></a>

#### stop\_autosync

```python
@locked
def stop_autosync()
```

Stops the internal watchdog timer

<a id="RS.fbd.FileBackedDict.is_autosyncing"></a>

#### is\_autosyncing

```python
@locked
def is_autosyncing() -> bool
```

Returns whether or not the internal watchdog timer is ticking

<a id="RS.fbd.FileBackedDict.writeback"></a>

#### writeback

```python
@locked
def writeback(topkey: str, *, only_if_dirty: bool = True, clean: bool = True)
```

Writes back a top-level key

<a id="RS.fbd.FileBackedDict.readin_modified"></a>

#### readin\_modified

```python
@locked
def readin_modified()
```

Reads in top-level keys that have been changed

<a id="RS.fbd.FileBackedDict.readin"></a>

#### readin

```python
@locked
def readin(topkey: str)
```

Reads in a top-level key

<a id="RS.fbd.FileBackedDict.bettergetter"></a>

#### bettergetter

```python
def bettergetter(key: Key,
                 default: typing.ForwardRef('FileBackedDict.Behavior.RAISE')
                 | typing.Any = Behavior.RAISE,
                 set_default: bool = True) -> Deserialized | typing.Any
```

Gets the value of key
    If the key is missing, then:
        if default is Behavior.RAISE: raises KeyError
        otherwise: returns default, and if set_default is truthy then sets the key to default

<a id="RS.fbd.FileBackedDict.get"></a>

#### get

```python
@locked
def get(key: Key,
        default: typing.ForwardRef('FileBackedDict.Behavior.RAISE')
        | Serializable = Behavior.RAISE,
        *,
        _tree: MutableMapping | None = None) -> Deserialized
```

Gets the value of key
    If the key is missing, then raises KeyError if default is Behavior.RAISE, otherwise returns default

<a id="RS.fbd.FileBackedDict.setitem"></a>

#### setitem

```python
@locked
def setitem(key: Key,
            val: Serializable,
            *,
            _tree: MutableMapping | None = None)
```

Sets a key to a value

<a id="RS.fbd.FileBackedDict.contains"></a>

#### contains

```python
@locked
def contains(key: Key, *, _tree: MutableMapping | None = None) -> bool
```

Returns whether or not the key exists

<a id="RS.fbd.FileBackedDict.items_full"></a>

#### items\_full

```python
@locked
def items_full(
    start_key: Key,
    key_join: bool = True
) -> typing.Generator[tuple[str | tuple[str, ...], Deserialized], None, None]
```

Iterates over every (key, value) pair, yielding the entire key

<a id="RS.fbd.FileBackedDict.items_short"></a>

#### items\_short

```python
@locked
def items_short(start_key: Key)
```

Iterates over every (key, value) pair, yielding the last part of the key

<a id="RS.fbd.FileBackedDict.keys"></a>

#### keys

```python
@locked
def keys(
    start_key: Key | None = None,
    key_join: bool = True
) -> typing.Generator[str | tuple[str, ...], None, None]
```

Iterates over every key

<a id="RS.fbd.FileBackedDict.values"></a>

#### values

```python
@locked
def values(start_key: Key) -> typing.Generator[[Deserialized], None, None]
```

Iterates over every value

<a id="RS.fbd.INIBackedDict"></a>

## INIBackedDict Objects

```python
class INIBackedDict(FileBackedDict[_INI_Serializable, _INI_Serialized,
                                   _INI_Deserialized])
```

A FileBackedDict implementation that uses ConfigParser as a backend

<a id="RS.fbd.INIBackedDict.sort"></a>

#### sort

```python
def sort(by: typing.Callable[[str | tuple[str, ...]],
                             typing.Any] = lambda k: k)
```

Sorts the data of this INIBackedDict in-place, marking all touched sections as dirty

<a id="RS.fbd.JSONBackedDict"></a>

## JSONBackedDict Objects

```python
class JSONBackedDict(FileBackedDict[_JSON_Serializable, _JSON_Serialized,
                                    _JSON_Deserialized])
```

A FileBackedDict implementation that uses JSON as a backend

<a id="RS.fbd.JSONBackedDict.sort"></a>

#### sort

```python
def sort(by: typing.Callable[[tuple[str, ...]], typing.Any] = lambda k: k)
```

Sorts the data of this JSONBackedDict (semi-)in-place, marking all touched sections as dirty

