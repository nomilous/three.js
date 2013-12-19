* This components directory houses a set of git sub repos, each a [component](https://github.com/component/component)
* The subrepos can be cloned using [git-seed](https://github.com/nomilous/git-seed) (i think) `git seed clone` or 'git seed pull'
* The Makefile in this directory updates each component repo, `git seed status` will inform changes across all sub repos
* **run git seed from the root if this repo** where the .git-seed file is. 