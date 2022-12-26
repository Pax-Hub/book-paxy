# Package Manifest

The package manifest is split into three parts. First, we have the base package. A package contains multiple flavors, each flavor contains multiple versions.

Package metadata is specified in essentially any file format, however, examples in this file will be in `toml`. Many other formats are supported, and translations to those file formats can be found in [Manifest Formats](./formats.md). Structure goes as follows:
```toml
[package]
name = "package-name"
description = "A package description"
authors = ["Author Name <Author Email>"]
license = "License"
homepage = "https://example.com"
repository = "https://example.com"
documentation = "https://example.com"
readme = "README.md"
keywords = ["keyword1", "keyword2"]

[dependencies]
dependency1 = "1.0.0"
dependency2 = {
    version = "1.0.0",
    flavor = "flavor"
}

[flavors]
flavor = "path/to/flavor.toml"
```

### `package`
The `package` table contains metadata about the package itself. The following fields are supported (* = required):
- `name`*: The name of the package. This is the name that will be used to refer to the package in other packages' manifests, as well as by users during installation.
- `description`*: A description of the package. This should be a short description of what the package does.
- `authors`: A list of authors of the package. This should be a list of git identifiers (`Name (Domain) <Email>`).
- `license`: The license of the package. This should be a valid SPDX license identifier.
- `homepage`: The homepage of the package. This should be a URL to the package's homepage.
- `repository`: The repository of the package. This should be a URL to the package's repository.
- `documentation`: The documentation of the package. This should be a URL to the package's documentation.
- `readme`: The readme of the package. This should be a path to the package's readme from the directory the manifest is in.
- `keywords`: A list of keywords for the package. These keywords should describe the package.

### `dependencies`
The `dependencies` table lists all dependencies that are required for all flavors of the package. Each entry should point to either a version or a table with `version` and `flavor` fields.

### `flavors`
The `flavors` table lists all flavors of the package. Each entry contain a path to a flavor manifest.

## Flavor Manifests
Each flavor specifies its own metadata, dependencies, and all versions of itself.
```toml
[flavor]
description = "A flavor description"
authors = ["Author Name <Author Email>"]
license = "License"
homepage = "https://example.com"
repository = "https://example.com"
documentation = "https://example.com"
readme = "README.md"

[versions]
"0.1.0" = "path/to/0.1.0.toml"
```

### `flavor`
The `flavor` table contains metadata about the flavor itself. The following fields are supported (* = required):
- `description`*: A description of the flavor. This should explain the differences between this flavor and other flavors of the same package.
- `license`, `homepage`, `repository`, `documentation`, `readme`: The same as in the `package` table. Only include if they're different from the package's.

### `versions`
The `versions` table lists all versions of the flavor. Each entry should point to a version manifest.

## Version Manifests
You're almost at the end. You've created a package, and you've created a flavor. Now you need to create a version. This is the last step in creating a package. A version manifest contains all the information necessary to install a specific version of a package.
```toml
[version]
authors = ["Author Name <Author Email>"]
license = "License"
homepage = "https://example.com"
repository = "https://example.com"
documentation = "https://example.com"
readme = "README.md"

[step1]
type = "clone"
url = "https://example.com"
branch = "master"
commit = "1234567890abcdef"

[step2]
type = "copy"
source = "path/to/source"
destination = "path/to/destination"

[step3]
type = "run"
command = "command"

[install]
steps = ["step1", "step2", "step3"]
artifacts = ["path/to/artifact1", "path/to/artifact2"]

[dependencies]
dependency1 = "1.0.0"
dependency2 = {
    version = "1.0.0",
    flavor = "flavor"
}
```

### `version`
All of the fields under `version` need only be specified if they different from the prior manifests.

### `dependencies`
The `dependencies` table lists all dependencies that are required for this version of the flavor. Each entry should point to either a version or a table with `version` and `flavor` fields.

## `install`
### `steps`
Takes a list of steps. Each step is a key in the manifest. The steps are executed in the order they are listed. The following step types are supported (* = required):
- `clone`: Clones a repository. The following fields are supported:
    - `url`*: The URL of the repository to clone.
    - `branch`: The branch to clone. Defaults to `master`.
    - `commit`: The commit to clone. Defaults to the latest commit on the branch.
- `copy`: Copies a file or directory. The following fields are supported:
    - `source`*: The source of the file or directory to copy.
    - `destination`*: The destination of the file or directory to copy.
- `run`: Runs a shell command. The following fields are supported:
    - `command`*: The command to run.

All install steps are run in an isolated environment without root access, and artifacts should be installed to the local directory.

### `artifacts`
Artifacts is a list of paths to files or directories that should be installed. These paths are relative to the local directory. All listed artifacts will be symbolically linked to the target directory.
