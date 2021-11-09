# The `build2` Project Roadmap

The aim of this document is to lay out the current `build2` project roadmap.

We divide all planned features or *areas of work* into three categories:
*"Strategic/Foundational"*, *"Important"*, and *"Nice to Have"*. Normally, we
try to make progress on at least one Strategic/Foundational area in every
release, though sometimes we have cleanup releases where the primarily focus
is on fixing bugs, paying off accumulated technical debt, etc.

The two common labels you will find next to some features are **[WIP]**
meaning the feature is being actively worked on (and you are welcome to start
experimenting with it) as well as **[HELP]** meaning the feature needs help
from the broader community in the form of feedback, expertise (for example,
knowledge and experience using a language or tool we are trying to support),
and/or actual implementation before it can go forward. Note that this doesn't
mean we don't want help on other features, of course. See also
[Contributing](https://build2.org/community.xhtml#contribute) for other ways
to contribute to the `build2` project.


## Strategic/Foundational

- **Conditional dependencies and dependency configuration [WIP]**

  Sometimes our projects only need a dependency if certain conditions are met
  (for example, we are building for Windows). Similarly, sometimes we may need
  a dependency configured in a certain way (for example, we need a specific
  feature enabled).

- **Dynamic dependencies in ad hoc recipes and rules [WIP]**

  Dynamic dependencies are supported in rules written in C++ but not in ad hoc
  recipes and rules written in Buildscript. The plan is to extend the
  Buildscript `depdb` builtin to support dynamic dependencies, including
  auto-generated.

- **C++20 modules [WIP] [HELP]**

  This is an ongoing effort that is currently blocked by support for modules
  in the compilers.

  Specifically, for GCC we have [complete C++20 modules
  support](https://build2.org/blog/build2-cxx20-modules-gcc.xhtml) sans the
  ability to handle auto-generated headers. However, the modules support in
  the compiler itself is not yet in a usable state. We also plan to try to
  generalize the module mapper with support for auto-generated headers along
  the [P1842](https://wg21.link/P1842R0) lines.

  For Clang we are waiting for the module mapper which is work in progress.

  Finally, for MSVC we need to understand if it's possible to provide
  sensible and conforming support without the module mapper (which the MSVC
  developers have decided not to provide).

  If you would like to help move things forward on any of these three fronts,
  get in touch.

- **Distributed compilation and caching for C/C++ [WIP]**

  We already have a lot of the infrastructure work in place. Specifically, all
  our compilation goes through partial preprocessing (full preprocessing on
  MSVC) and we have an accurate idea of all the inputs to each translation
  unit (headers, modules, compiler options, TU tokens themselves, etc) as well
  as which of them have changed.

- **Automatic distribution package generation**

  We would like to be able to automatically produce binary distribution
  packages (`.deb`, `.rpm`, `.msi`, etc) from `build2` packages and maybe even
  publish them to [`cppget.org`](https://cppget.org).

- **Documentation [WIP]**

  This includes the documentation for the missing pieces of the toolchain
  itself (mostly the build system) as well as the documentation extraction
  (from source code) that everyone can use to document their build system
  modules (and maybe C++ projects in general).

## Important

- **Assembler support [HELP]**

  We need first-class assembler support in the `bin`/`cc` modules. See
  [issue #162](https://github.com/build2/build2/issues/162) for background.

- **Autoconf emulation module [HELP]**

  We have started work on
  [`libbuild2-autoconf`](https://github.com/build2/libbuild2-autoconf/), a
  build system module that provides a rule for processing GNU Autoconf
  `config.h.in` files as well as their CMake and Meson flavors. We need help
  populating it with built-in checks.

- **Lockfile**

  We would like the package manager to provide the lockfile functionality.

- **Config initializer**

  We would like to have a higher-level (than compiler options) mechanism for
  specifying the desired configuration.

  See [issue #11](https://github.com/build2/build2/issues/11).

- **Support for static analysis [HELP]**

  We would like to have a general approach for running static analysis tools.

  See [issue #30](https://github.com/build2/build2/issues/30) for some
  background as well as to contribute usage experience, ideas, etc.

- **Incremental testing**

  We would like to be able to run tests only for targets that have changed.
  This will rely heavily on our existing work on Testscript, specifically,
  the fact that the test inputs/outputs are well-encapsulated.


## Nice to Have

See the [Issues List](https://github.com/build2/build2/issues/) for some
of the nice-to-have features.
