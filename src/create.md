# Creating a Package

## Before You Begin
Consider the following items:
- Does this package already exist?
    - If so, are you uploading a specific version? Add a version to the original package instead.
- Does this package contain everything necessary for it to work?

## What should a package have?
A package should contain the following:
- The package itself
- Any pieces of the package that are necessary for use.

For example, consider the `rust` package. It downloads `rustup`, then uses `rustup` to install `rustc` and `cargo`. This provides a complete rust environment.

## Package Versions
Package versions should correspond to versions of the actual software. For example, version 3.6 of `python` should install python 3.6. Package maintainers should make an effort to provide all versions of a package (automatic deployment of non-breaking versions is recommended).

## Package Flavors
Package flavors are often provided in the form of a specific architecture. For example, `rust` uses metadata for the target triple. A package should provide metadata for anything that seems relevant. In other cases, package flavors specify the origin of the package. For example, `jdk` provides `openjdk` and `oracle`.

## Package Names
A package name should reflect what's inside the package. If the package provides a single executable, it should be named for that executable. Otherwise, if a package provides a collection of software, like `gcc`, it should be named after the cannonical name for that software. In addition, if there are multiple sources for said software, like Java JDKs, they should be specified in the package flavors.

## Begin
Now that you have considered all of these, you may continue on to the next section to begin your package.
