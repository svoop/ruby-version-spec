# Brainstorming the Specs of .ruby-version

## Living Specification

* The file contains exactly one line.
* The trailing newline character is optional.
* The full notation is `ENGINE-VERSION` e.g. `jruby-3.2.2`
* The separator between ENGINE and VERSION is exactly one dash `-`
* If the ENGINE and separator are omitted, the default engine is `ruby` (MRI).
* The VERSION is either strict or relaxed:
  * Strict versions refer to a specific MAJOR.MINOR.PATCH version e.g. `3.2.2` or `3.3.0-rc2`
  * Relaxed versions omit the patch version digits e.g. `3.2` and refer to the latest corresponding patch version available in the current context. (Say, the latest release of the `3.2` branch is `3.2.2`, but you've only installed `3.2.1`. In this case, the relaxed version `3.2` would cause the Ruby version manager to use `3.2.1`)

## Discussion

To join the discussion, [head over here](https://github.com/rubygems/rubygems/discussions/7074).
