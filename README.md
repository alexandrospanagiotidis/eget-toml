# eget configuration

- Put [eget](https://github.com/zyedidia/eget) into `$PATH`
- Set `EGET_GITHUB_TOKEN=...` in `.env`
    - Use existing token or create one: [GitHub token](https://github.com/settings/tokens)
    - Do not commit `.env` (should be ignored already)
- `direnv allow`
- `eget -D`
