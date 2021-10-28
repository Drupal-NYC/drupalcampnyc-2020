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
$ lando drush en tome tome_static
```

Export the Drupal site.

```
$ lando drush tome:export -y
$ lando drush tome:static --uri=https://2020.drupalcamp.nyc
```

This exports the static HTML site to the `html` directory in the project root.

Then you need to deploy that to a new repo on GitHub, configured appropriately for GitHub Pages.

For more details, refer to the Tome documentation:

### Install Tome:

https://tome.fyi/docs/installing-existing-site/

### Tome docs on GitHub Pages setup:

https://tome.fyi/docs/hosting/github-pages/

Some details in this Tome walkthrough may be outdated (compare with new docs at https://pages.github.com).

There's also a Tome GitHub Pages project template here:

https://github.com/drupal-tome/subdir-test

