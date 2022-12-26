# The Basics

### Installing a package
- If you know the name<br>
`paxy install {name}` installs a given package or packages by name.
- If you don't know the name<br>
`paxy search {query}` searches for a package by name or description.
> Note: `add` works as an alias for `install`.

### Updating a package
`paxy update {name}` updates a given package or packages by name Alternatively, `paxy` by itself updates the entire system.
> Note: `upgrade` works as an alias for `update`.

### Removing a package
`paxy remove {name}` removes a given package or packages by name.
> Note: `uninstall` works as an alias for `remove`.

### Listing packages
`paxy list` lists all installed packages.

### Automatic correction
For all commands, `paxy` will automatically correct typos and abbreviations. For example, imagine a scenario where `bash` isn't installed, but `sh` is. `paxy remove bash` will provide you with a prompt: "Did you mean 'sh'? [Y/n]". If you answer "Y", `paxy` will remove `sh` instead.
> Warning: please don't remove sh. That is a horrible idea.
