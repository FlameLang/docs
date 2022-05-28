# Modules

Flame has a very simple zero-configuration module system based on `use` expressions.

Modules are supposed to be immutable so they are cached and hashed.
You can force a refetch using a flag.
If Flame detects that a module has changed (i.e. it has a different hash) it will warn you and ask if you want to proceed.

