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

- **Distributed compilation and caching for C/C++ [WIP]**

  We already have a lot of the infrastructure work in place. Specifically, all
  our compilation goes through partial preprocessing (full preprocessing on
  MSVC) and we have an accurate idea of all the inputs to each translation
  unit (headers, modules, compiler options, TU tokens themselves, etc) as well
  as which of them have changed.

- **Documentation [WIP]**

  This includes the documentation for the missing pieces of the toolchain
  itself (mostly the build system) as well as the documentation extraction
  (from source code) that everyone can use to document their build system
  modules (and maybe C++ projects in general).

## Important

- **Assembler support [HELP]**

  We need first-class assembler support in the `bin`/`cc` modules. See
  [issue #162](https://github.com/build2/build2/issues/162) for background.

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
