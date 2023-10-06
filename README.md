# action-update-pot

[![Chat on Matrix](https://img.shields.io/matrix/Gradience:matrix.org?color=%230dbd8b&label=Gradience&logo=matrix&logoColor=white)](https://matrix.to/#/#Gradience:matrix.org)
[![Chat on Discord](https://dcbadge.vercel.app/api/server/4njFDtfGEZ?style=flat&theme=default-inverted)](https://discord.com/invite/4njFDtfGEZ)

Github Action for updating .pot

## Usage

### Example usage

```shell

name: "Translation"

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
  schedule:
    - cron: '21 6 * * 5'

jobs:
  update-pot:
    name: Update .pot
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Update .pot
        uses: GradienceTeam/action-update-pot@main
        with:
          title: "Gradience POT file"
          copyright: "Gradience Team"
          license: "GNU GPLv3"
          author: "Gradience Team"
          commiter: "Gradience Bot"
          commiter_email: "AdwCustomizerTeam@proton.me"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Parameters

You must also provide an `GITHUB_TOKEN` in `env`

| Name               | Description                                                               | Default            | Required |
| ------------------ | ------------------------------------------------------------------------- | ------------------ | -------- |
| `destination_path` | Destination path to save generated .pot file                              | `/po`              | false    |
| `slug`             | Project slug. Defaults to the Github repository name.                     | $GITHUB_REPOSITORY | false    |
| `text_domain`      | Text domain to look for in the source code. Defaults to the project slug. | `slug`               | false    |
| `author`           | Replace "FIRST AUTHOR <EMAIL@ADDRESS>"'                                   |                    | false    |
| `commiter`           |    Setting committer                          | `github-actions[bot]`              | false
| `commiter_email`           |   Setting committer email                           | `41898282+github-actions[bot]@users.noreply.github.com`              | false
| `title`            | Replace "SOME DESCRIPTIVE TITLE."'                                        |                    | false    |
| `copyright`        | Replace "YEAR THE PACKAGE S COPYRIGHT HOLDER"'                            |                    | false    |
| `license`          | Replace "same license as the PACKAGE package"'                            |                    | False    |
