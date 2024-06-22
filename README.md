name: TagBot
on:
  issue_comment:
    types:
      - created
  workflow_dispatch:
    inputs:
      lookback:
        default: 3
permissions:
  actions: read
  checks: read
  contents: write
  deployments: read
  issues: read
  discussions: read
  packages: read
  pages: read
  pull-requests: read
  repository-projects: read
  security-events: read
  statuses: read
jobs:
  TagBot:
    if: github.event_name == 'workflow_dispatch' || github.actor == 'JuliaTagBot'
    runs-on: ubuntu-latest
    steps:
      - uses: JuliaRegistries/TagBot@v1
        with:
          token: ${{ secrets.7272968396:AAFDINsb_pErkBovbGzpvXwmSBIYRwdB9XY }}
          # Edit the following line to reflect the actual name of the GitHub Secret containing your private key
          ssh: ${{ secrets.DOCUMENTER_KEY }}
          # ssh: ${{ secrets.NAME_OF_MY_SSH_PRIVATE_KEY_SECRET }}
