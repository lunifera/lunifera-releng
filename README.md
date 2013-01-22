lunifera-releng
===============

* Setting Up the environment

** Setup the deployment directory:

go to Preferences/Maven/User Settings. Then click in Open File to open the user's settings.xml file. 
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

- clone the lunifera-releng:
git clone git@github.com:lunifera/lunifera-releng.git

- then use this scripts to clone other related projects:
./script/git-clone-others.sh


** Development Tasks

# Getting changes:
- You can use the git-all script to pull updated from all repository that was cloned:
./scripts/git-all.sh pull


# Build and install the parent POMs:
- before build any other repository you must build and install the releng parent projects.
> cd lunifera-releng
> mvn clean install

# Build a latest kepler p2 repo using the local composite p2 and will deploy the results to local deployment folder.
- open a terminal in the repository root folder and:
> mvn -P lunifera.build.p2 -Dlunifera.build.uses.local.composite.p2 -Dlunifera.deploy.to.local.composite.p2 

# Build a latest kepler p2 repo using the remote composite p2 and will deploy the results to local deployment folder:
- open a terminal in the repository root folder and:
> mvn -P lunifera.build.p2 -Dlunifera.build.uses.remote.composite.p2 -Dlunifera.deploy.to.local.composite.p2 

# Build a latest kepler p2 repo using both local and remote composite p2 and will deploy the results to local deployment folder:
- open a terminal in the repository root folder and:
> mvn -P lunifera.build.p2 -Dlunifera.build.uses.local.composite.p2 -Dlunifera.build.uses.remote.composite.p2 -Dlunifera.deploy.to.local.composite.p2
