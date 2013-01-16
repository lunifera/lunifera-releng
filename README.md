lunifera-releng
===============

- clone the lunifera-releng:
git clone git@github.com:lunifera/lunifera-releng.git

- use this scripts to clone other related projects:
./script/git-clone-others.sh

- use this script to pull from each repo:
./script/git-all.sh pull

- use this to build all project's p2 for kepler:
./script/mvn-all.sh -P p2-kepler

- use this to build all project's p2 for kepler and copy the generated P2 to <dir> folder:
./script/mvn-all.sh -P p2-kepler -D LUNIFERA-DEPLOY-DIR=<dir>

If desired the LUNIFERA-DEPLOY-DIR property could be set in the maven's settings.xml file as this:

  <profile>
      <id>lunifera-dev</id>

      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>

      <properties>
        <LUNIFERA-DEPLOY-DIR>/User/myuser/mydir</LUNIFERA-DEPLOY-DIR>
      </properties>
    </profile>
  </profiles>
 