# Brainstorming the Specs of .ruby-version

## Living Specification

* Only the first line not starting with `#` is read, all other lines are ignored.
* The trailing newline character on the last (and possibly only) line is optional.
* The full notation is `RUNTIME-VERSION` e.g. `jruby-3.2.2`
* The separator between RUNTIME and VERSION contains  dash(es) or witespace(s) only: `/[-\s]+/`
* If the RUNTIME and separator are omitted, the default runtime is `ruby` (MRI).
* The VERSION is either strict or relaxed:
  * Strict versions refer to a specific version e.g. `3.2.2` or `3.3.0-rc2`
  * Relaxed versions omit the minor version digit e.g. `3.2` and refer to the latest corresponding minor version available in the current context. (Say, the latest release of the `3.2` branch is `3.2.2`, but you've only installed `3.2.1`. In this case, the relaxed version `3.2` would cause the Ruby version manager to use `3.2.1`)

## Discussion

To join the discussion, [head over here](https://github.com/rubygems/rubygems/discussions/7074).
