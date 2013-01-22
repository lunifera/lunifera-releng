lunifera-releng
===============

## Setting up the development environment
---------------------------------------

###1. Set the deployment directory:

Go to Preferences/Maven/User Settings. Then click in Open File to open the user's settings.xml file.
In the opened file created a new profile, include the property lunifera.deployment.root.dir and set a value for it. see this example:

    <profiles>
      <profile>
        <id>lunifera-dev</id>
        <activation>
          <activeByDefault>true</activeByDefault>
        </activation>
        <properties>
          <lunifera.deployment.root.dir>/User/myuser/myRootDeploymentDir</lunifera.deployment.root.dir>
        </properties>
      </profile>
    </profiles>

###2. Clone the source repositories:
- to be able to contribute you must fork the lunifera's github repositories and clone from them.
> git clone git@github.com:lunifera/lunifera-releng.git

- then use this scripts to clone other related projects:
> ./scripts/git-clone-others.sh

###3. Build and install the parent POMs:
- before build any other repository you must build and install the releng parent projects.
> cd lunifera-releng
> mvn clean install


## Development Tasks

### Getting source changes:
- You can use the git-all script to pull updated from all cloned repositories:

> ./scripts/git-all.sh pull

### Build a latest kepler p2 repo using the remote composite p2. 
- open a terminal in the repository root folder and type this:
> mvn -P lunifera.build.p2 -Dlunifera.build.uses.remote.composite.p2

- The remote composite.p2 is the default, so the property 'lunifera.build.uses.remote.composite.p2' can be omited.
> mvn -P lunifera.build.p2


### Build a latest kepler p2 repo using the remote composite p2 and deploying the results to local deployment folder.
- open a terminal in the repository root folder and type this:

> mvn -P lunifera.build.p2 -Dlunifera.build.uses.remote.composite.p2 -Dlunifera.deploy.to.local.composite.p2 


### Build a latest kepler p2 repo using the local composite p2 and deploying the results to local deployment folder.
- open a terminal in the repository root folder and type this:

> mvn -P lunifera.build.p2 -Dlunifera.build.uses.local.composite.p2 -Dlunifera.deploy.to.local.composite.p2


### Build a latest kepler p2 repo using both local and remote composite p2 and deploying the results to local deployment folder:
- open a terminal in the repository root folder and type this:

> mvn -P lunifera.build.p2 -Dlunifera.build.uses.local.composite.p2 -Dlunifera.build.uses.remote.composite.p2 -Dlunifera.deploy.to.local.composite.p2

