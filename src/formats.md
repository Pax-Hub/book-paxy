# Manifest Formats

Package manifests can be written in nearly any language. The following are all directly supported, but more could be implemented with little difficulty. The only requirement is a rust `serde` implementation.

## toml

The default format for manifests is toml. This is the format used in the examples in this book.

## json
### Package Manifest
```json
{
    "package": {
        "name": "package-name",
        "description": "A package description",
        "authors": ["Author Name <Author Email>"],
        "license": "License",
        "homepage": "https://example.com",
        "repository": "https://example.com",
        "documentation": "https://example.com",
        "readme": "README.md",
        "keywords": ["keyword1", "keyword2"]
    },
    "dependencies": {
        "dependency1": "1.0.0",
        "dependency2": {
            "version": "1.0.0",
            "flavor": "flavor"
        }
    },
    "flavors": {
        "flavor": "path/to/flavor.json"
    }
}
```
### Flavor Manifest
```json
{
    "flavor": {
        "description": "A flavor description",
        "authors": ["Author Name <Author Email>"],
        "license": "License",
        "homepage": "https://example.com",
        "repository": "https://example.com",
        "documentation": "https://example.com",
        "readme": "README.md"
    },
    "versions": {
        "0.1.0": "path/to/0.1.0.json"
    }
}
```
### Version Manifest
```json
{
    "version": {
        "authors": ["Author Name <Author Email>"],
        "license": "License",
        "homepage": "https://example.com",
        "repository": "https://example.com",
        "documentation": "https://example.com",
        "readme": "README.md"
    },
    "step1": {
        "type": "clone",
        "url": "https://example.com",
        "branch": "master",
        "commit": "1234567890abcdef"
    },
    "step2": {
        "type": "copy",
        "source": "path/to/source",
        "destination": "path/to/destination"
    },
    "step3": {
        "type": "run",
        "command": "command"
    },
    "install": {
        "steps": ["step1", "step2", "step3"],
        "artifacts": ["path/to/artifact1", "path/to/artifact2"]
    }
    "dependencies": {
        "dependency1": "1.0.0",
        "dependency2": {
            "version": "1.0.0",
            "flavor": "flavor"
        }
    }
}
```

## yaml
### Package Manifest
```yaml
package:
    name: package-name
    description: A package description
    authors:
        - Author Name <Author Email>
    license: License
    homepage: https://example.com
    repository: https://example.com
    documentation: https://example.com
    readme: README.md
    keywords:
        - keyword1
        - keyword2
dependencies:
    dependency1: 1.0.0
    dependency2:
        version: 1.0.0
        flavor: flavor
flavors:
    flavor: path/to/flavor.yaml
```
### Flavor Manifest
```yaml
flavor:
    description: A flavor description
    authors:
        - Author Name <Author Email>
    license: License
    homepage: https://example.com
    repository: https://example.com
    documentation: https://example.com
    readme: README.md
versions:
    "0.1.0": path/to/0.1.0.yaml
```
### Version Manifest
```yaml
version:
    authors:
        - Author Name <Author Email>
    license: License
    homepage: https://example.com
    repository: https://example.com
    documentation: https://example.com
    readme: README.md
step1:
    type: clone
    url: https://example.com
    branch: master
    commit: 1234567890abcdef
step2:
    type: copy
    source: path/to/source
    destination: path/to/destination
step3:
    type: run
    command: command
install:
    steps:
        - step1
        - step2
        - step3
    artifacts:
        - path/to/artifact1
        - path/to/artifact2
dependencies:
    dependency1: 1.0.0
    dependency2:
        version: 1.0.0
        flavor: flavor
```
