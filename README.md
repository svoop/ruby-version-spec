# Brainstorming the Specs of .ruby-version

## Specification Draft

* The file contains exactly one line.
* The trailing newline character is optional.
* The full notation is `ENGINE-VERSION` e.g. `jruby-3.2.2`
* The separator between ENGINE and VERSION is exactly one dash `-`
* The ENGINE may contain one or multiple build config flags added with a plus `+` e.g `truffleruby+graalvm`
* If the ENGINE and separator are omitted, the default engine is `ruby` (MRI).
* The VERSION is either strict or relaxed:
  * Strict versions refer to a specific MAJOR.MINOR.PATCH version e.g. `3.2.2` or `3.3.0-rc2`
  * Relaxed versions omit the patch version digits e.g. `3.2` and refer to the latest corresponding patch version available in the current context. (Say, the latest release of the `3.2` branch is `3.2.2`, but you've only installed `3.2.1`. In this case, the relaxed version `3.2` would cause the Ruby version manager to use `3.2.1`)

## Discussion

To join the discussion, [head over here](https://github.com/rubygems/rubygems/discussions/7074). Here are some of the arguments that have emerged so far:

* `.ruby-version` has been introduced as a way to declare the "Ruby version currently used for development" and this should remain its primary function.
* When using it e.g. to lock a Ruby version in a bundler Gemfile with `ruby: file: ".ruby_version"`, you lose the ability to declare a relaxed version.
* The above also applies when it is used to select a Ruby for deployment. However, you're encouraged to rely on the locked Ruby version in `Gemfile.lock` or `gems.locked` instead.
* Allowed engines are not part of the specification, but should be listed informally in a guide/FAQ accompanying the specification.

## Questions

* Parsing of `.ruby-version` could be simplified by making the ENGINE mandatory. It should be the Ruby version manager maintainers call to decide whether they want to adopt such a change though.
