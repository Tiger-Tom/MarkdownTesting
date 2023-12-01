# `Bootstrapper` (shorthand: `RS.BS`)

## method access_entrypoint(ep: str) -> types.ModuleType
> Loads the entrypoint's surrounding module

## method bootstrap(close_after: bool = True)
> Executes the base manifest, then accesses, assigns, and chainloads the entrypoint

## method chainload_entrypoint(rs: Callable)
> Runs the entrypoint's __call__ method

## method close(do_exit: bool | int = False)
> Executes all shutdown callbacks and closes logging (logging.shutdown()), and exits with exit code do_exit if it isn't False

## classmethod ensure_python_version()
> Ensure that the Python version meets the minimum requirements

## method parse_arguments(args=None)
> Generate and ArgumentParser and parse (known) arguments

## method register_onclose(cb: Callable)
> Registers a function to run when self.close() is called

## method run_base_manifest()
> Executes the base manifest (_rsruntime/MANIFEST.ini)

## method setup_logger() -> logging.Logger
> Sets up self.logger, as well as logging.INFOPLUS/IRRECOVERABLE and Logger.infop/irrec()

## method stage_entrypoint(rs_outer: types.ModuleType) -> rs_outer.RunServer
> Initializes the entrypoint's class (with self as an argument)
