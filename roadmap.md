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

- **Build system modules [WIP] [HELP]**

  Dynamically buildable/loadable modules that can be used to extend the
  build system with support for additional languages, code generators,
  etc.

  This feature is already in a fairly advanced stage and you can begin looking
  into writing modules. See
  [`libbuild2-hello`](https://github.com/build2/libbuild2-hello) to get
  started.

- **Project-specific configuration**

  We need to make the same configuration mechanisms we already use inside the
  build system available for custom, project-specific configuration.

- **C++20 modules [WIP] [HELP]**

  This is an ongoing effort that is currently blocked by support for modules
  in the compilers.

  Specifically, for GCC we have the
  [`cxx-modules-ex`](https://gcc.gnu.org/git/?p=gcc.git;a=shortlog;h=refs/heads/boris/c%2B%2B-modules-ex)
  branch which implements [P1703](https://wg21.link/P1703) and
  [P1842](https://wg21.link/P1842) and which will hopefully be eventually
  merged with Nathan's branch and/or master. For Clang we are waiting for the
  module mapper (for header unit and include translation support) as well as
  some sort of a strict modules mode in the `c++2a` mode, see [this discussion
  for details](http://lists.llvm.org/pipermail/cfe-dev/2019-October/063637.html).
  Finally, for MSVC we are waiting for header unit and include translation
  support hopefully in the form of the module mapper.

  If you are working on GCC or Clang and would like to help move things
  forward on the compilers front, get in touch.

- **Distributed compilation and caching for C/C++ [WIP]**

  We already have a lot of the infrastructure work in place. Specifically, all
  our compilation goes through partial preprocessing (full preprocessing on
  MSVC) and we have an accurate idea of all the inputs to each translation
  unit (headers, modules, compiler options, TU tokens themselves, etc) as well
  as which of them have changed.

- **Ad hoc build rules**

  Ability to write custom build rules directly in buildfiles using either a
  POSIX shell-like subset of portable commands or, for more complex cases,
  C++.

  See [issue #24](https://github.com/build2/build2/issues/24) for some
  background.

- **Build system overlays**

  Ability to overlay a directory tree with buildfiles over a parallel tree
  with source code. This feature will primarily be helpful while non-intrusively
  packaging third-party projects.

  See [issue #26](https://github.com/build2/build2/issues/26) for some
  background.

- **Documentation**

  This includes the documentation for the missing pieces of the toolchain
  itself (mostly the build system) as well as the documentation extraction
  (from source code) that everyone can use to document their build system
  modules (and maybe C++ projects in general).

## Important

- **Hermetic builds**

  We would like to have the ability to make a configuration hermetic/isolated
  from outside changes. This functionality would be an additional layer on
  top of high-fidelity builds that we already have.

- **Lockfile**

  We would like the package manager to provide the lockfile functionality.

- **Config initializer**

  We would like to have a higher-level (than compiler options) mechanism for
  specifying the desired configuration.

  See [issue #11](https://github.com/build2/build2/issues/11).

- **Conditional dependencies and package components**

  This will be our answer to the "How do I only have this dependency on
  certain platforms (or, more generally, in certain configurations)?" and
  "How do I make some parts/configurations of my package optional?" type
  of questions.

  See [issue #41](https://github.com/build2/build2/issues/41) for some
  background.

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
