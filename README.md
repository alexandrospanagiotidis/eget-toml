# eget configuration

- Put [eget](https://github.com/zyedidia/eget) into `$PATH`
- Set `EGET_GITHUB_TOKEN=...` in `.env`
    - Use existing token or create one: [GitHub token](https://github.com/settings/tokens)
    - Do not commit `.env` (should be ignored already)
- `direnv allow`
- `eget -D`


## eget always downloads with `upgrade_only=true` even if no newer file

It [seems](https://github.com/zyedidia/eget/blob/master/eget.go#L121) that `eget` looks for a target file with the same name as the Github project to determine if there is a newer version.

For example, for `BurntSushi/ripgrep`, `eget` looks for a file called `ripgrep`.
Since `ripgrep` gets extracted to `rg`, the update check always fails, and `eget` will always install it.

One fix is using `target` to specify the target filename, e.g.,
```ini
["BurntSushi/ripgrep"]
target = "~/.local/bin/rg"
```

You could also create a symlink if you want to keep both names, e.g.,
```shell
$ ln -s ~/.local/bin/rg ~/.local/bin/ripgrep
```
