# Fork Updater
This repository functions to run several github actions jobs to update repository forks. The jobs follow the following template:

```yaml
jobs:
  fork-name:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
      with:
        repository: maly7/$FORK_NAME
        token:  ${{ secrets.TOKEN }}
    - run: |
        git remote add upstream $FORK_URL
        git fetch upstream
        git merge upstream/master
        git push
```
