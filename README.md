# archery

Archery is the global styles for humanization and personalization, hitting the target on everything.

## Concept

All client side web applications that reside under the mywiserhealth.com domain and branding will use archery as a shared global syle and design asset resource.

This will allow for a single compiled style sheet for the entire domain.

Projects will become folders within archery with the root level main.less file importing those project specific files.

Global variables will be defined at the root level of archery and will be imported via the main.less file.


## Adding archery to your project

In the root of your project checkout, add the archery submodule. It should exist in your checkout as "archery".

```
git submodule add https://github.com/WiserTogether/archery.git
```

After the submodule is added to your project locally, you will need to add it to your repo as if you were adding and commit a file.

```
git add archery
git commit archery -m "Adding archery submodule"
git push
```

The archery code is now a submodule of your project.

## Updating code in archery

Remember that archery is just like any other project and developers may not commit directly into master.

First, you will want to check out a working copy of archery.  Do this at the sibling level where you have you other projects checked out.

```
git clone https://github.com/WiserTogether/archery.git
```

Now you may work with archery locally

```
cd archery
git fetch --all
git reset --hard origin/master
git checkout -b new_branch_name
```

Now you need to setup archery dependencies

```
sudo npm install
bower install
```

After that completes successfully, you will need to validate everything by building

```
grunt
```

This should create a structure similar to the one below in your /build folder

```
├── 404.html
├── css
│   └── ea2dd69f.main.css
├── favicon.ico
├── fonts
│   ├── 34c4b822.icons-9ee82a68db663a88e273228cd7483d91.eot
│   ├── 88358660.icons-9ee82a68db663a88e273228cd7483d91.ttf
│   └── f86b6b62.icons-9ee82a68db663a88e273228cd7483d91.svg
├── index.html
└── robots.txt
```

Now you may make changes to files within your branch and then

```
git commit -a -m "Commit message that reflects the work you did"
git push origin new_branch_name
```

Now you will need to create a pull request from that branch in github for it to be reviewed and merged into master.

After the code is merged into master you may update your project's ref for the submodule.


## Updating archery in your project

If changes were made in archery and you would like to associate those changes to your project you will need to udpate the submodule ref for your project.

```
cd your_project
git fetch --all
git reset --hard origin/master
git checkout -b new_branch_name
git submodule init
git submodule update
git commit archery -a -m "updating archery version for project"
git push origin new_branch_name
```

After updating the ref for archery in your project, you will need to submit a pull request from the branch in github into master for the updated archery version to be part of your application.


## Deploying archery

Archery, while using submodules for local development, will deploy as a stand alone static application.

The "/build" folder in archery, that is created by grunt, will be deployed to both the dev cnd and the production cdn. This will enable deployment of css independent of application code.

Travis will build and deploy to both of these environments as appropriate.
## Maintaining archery
