lunifera-releng
===============

- clone the lunifera-releng:
git clone git@github.com:lunifera/lunifera-releng.git

- use this scripts to clone other related projects:
./script/git-clone-others.sh

- use this script to pull from each repo:
./script/git-all.sh pull

- use this to build all project's p2 for kepler:
./script/mvn-all.sh clean verify -P p2-kepler
