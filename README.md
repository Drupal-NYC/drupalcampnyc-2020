# drupalcampnyc-2020

Static archive of 2020.drupalcamp.nyc

## Annual Archive

To archive the 2020 site, we used [the Tome module](https://www.drupal.org/project/tome) to export [a static site](https://2020.drupalcamp.nyc)
and created [a new git repository](https://github.com/Drupal-NYC/drupalcampnyc-2020/tree/main) to house it.

For future archivers' benefit: in a nutshell, the process is ...

### Run a Tome Static export using Drush

Pull database and files from Pantheon Live environment.

```
$ lando pull --code=none --database=live --files=live
```

Composer require Tome module.

```
$ lando composer require drupal/tome
```

Drush enable Tome Static submodule.

```
$ lando drush en tome_static
```

Export the Drupal site.

```
$ lando drush tome:export -y
$ lando drush tome:static --uri=https://2020.drupalcamp.nyc
```

Rename html directory to docs for GitHub Pages.

```
$ mv html docs
```

Push to `main` branch of a new GitHub repo. For example:

```
$ git add .
$ git commit -m "Commit the static site export to GitHub."
$ git remote add github git@github.com:hotwebmatter/tome-demo.git
$ git push -u github main
```

For more details, refer to the Tome documentation:

### Install Tome:

https://tome.fyi/docs/installing-existing-site/

### Tome docs on GitHub Pages setup:

https://tome.fyi/docs/hosting/github-pages/

**NOTE:** The GitHub Pages documentation for Tome is outdated; GitHub Pages now expects your static site to live [in the `main` branch](https://pages.github.com/).
