# `uv`

## Installation

```console
$ curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Upgrade

```console
$ uv self update
```

## Manage project-wide settings

### Create a uv project

```console
$ uv init
```

### Synchronies an existing project

```console
$ uv sync
```

## Manage packages in a uv project

### Add a package

```console
$ uv add <package>
```

??? tip "`--dev` flag"

    A common flag to use with `uv add` is the `--dev` flag. It signals the added
    package will is for development only.
    It will not be part of the requirement should the project be published as a 
    package.

### Upgrade an existing package

```console
$ uv add "package_name>=desired_version" --upgrade-package package_name
```

!!! example 
    ```console
    $ uv add "zensical>=0.0.43" --upgrade-package zensical
    ```

## Uninstallation

### Clean up stored data

```console
$ uv cache clean
$ rm -r "$(uv python dir)"
$ rm -r "$(uv tool dir)"
```

### Remove the `uv`, `uvx`, and `uvw` binaries

```console 
$ rm ~/.local/bin/uv ~/.local/bin/uvx
```

## References

- Documentation [homepage]

  [homepage]: https://docs.astral.sh/uv/