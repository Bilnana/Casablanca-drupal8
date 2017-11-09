# MCI Drupal 8 docker based boilerplate

This project is the base which can be easily used to start a new project.

The main idea is to use [docker](http://docker.com/) container technology and tools, [Docker4Drupal](http://docker4drupal.org/) project as a container base for Drupal 7 and 8 development and set of predefined structures and tools to streamline development, frontend build, testing and deployment.

## Quick start guide for MCI Drupal docker based boilerplate

If you wish to start as quickly as possible and need details, follow this [Quick start guide](docs/quickstart.md)

These two steps that are needed **just once** as they will serve all future projects:

1. **Local name resolving** configured as explained in [Resolving local domains](docs/resolving.md)
2. **Container name based routing** as explained in [Proxy containers to local domains](docs/proxy.md)

Essentially, in order to have the ability to use URL like http://myproject.loc you need to have:

3. **Project directory** with basic structure and needed configurations as explained in [here](#Files%20structure) with `git clone` or download and unzip this project as archive
4. **Change** project template name from `{{PROJ}}` to your real project name `mynewproject` which should be the same as parent directory name
5. **Change** where you want to keep database files and other options in `docker-compose.yml`
6. **Start the containers** with just in terminal in project directory with `docker-compose up -d`
7. **Docker** will be starting, downloading images if necessary, importing database
8. **Visit** your new local site at your URL like http://mynewproject.dev.loc
9. **Visit** your new phpMyAdmin at your URL like http://mynewproject.pma.loc

## Additional background information

For more detailed information, read these documents:

1. [Docker 101](docs/docker.md)
2. [Installing Docker](docs/install_docker.md)
3. [Resolving local domains](docs/resolving.md)
4. [Proxy containers to local domains](docs/proxy.md)
5. [Frontend tools](docs/frontend.md)
6. [Quick start](docs/quickstart.md)
7. [Using](docs/using.md)
8. [`dc` helper tool](https://gitlab.com/MacMladen/dc/)
9. [Terminal 101](docs/terminal101.md)
10. [Local install commands sequence](docs/local-docker.sh)
11. [Server install commands sequence](docs/server-docker.sh)

# Components

## Docker

There is somewhat detailed background on **why & how** about docker in [here](docs/docker.md)

### Proxy

**Docker4Drupal** project uses ports to communicate with browser. In order to make it more simple and use domain names, we chose to use [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy) container that dynamically scans docker network and proxies container so they are accessible by configuration/variable assigned name.

### Resolver

Resolving can be done most easily in `/etc/hosts` file but that requires editing every time we have new project so we developed **dnsmasq** based recipe that works on Linux and Mac (looking into Windows solution).

### Frontend tools

Front end build system is based on `node` and `npm` which set up local working build with `gulp` as task runner and **Sass** as main CSS preprocessor. **Sass** is developed in `/frontend` where are all the tools, libraries and unoptimized resources which are then compiled and optimized directly in theme according to `gulpfile.js` settings.

### `dc` tool

`dc` is **bash** based tool that just simplifies commands and procedures for managing projects. You can get it separately [here](https://gitlab.com/MacMladen/dc) but currently it is very specific for MCI workflow and yet has to be adapted for new workflow so it is useful only as preview what can and will be done.

## Files structure

* **assets** — this directory is intended to hold *all original** files given by the client. They should not be altered and, if needed, should be divided into subdirectories named by date they were given.
* **databases** — Here are all database dumps and this directory is mounted into `mariadb` container so all files are accessible to be sourced into database.
* **docker-runtime** — all docker persistent data is held here. That enables us to rebuild containers without loosing:
  - `/databases` database files,
  - `/metro` add theme to **phpMyAdmin** and to
  - `/drush` keep useful `drush` commands.
  - ...possibly something more in future
* **docroot** — this is for the **root** of the website, where all Drupal files are held. Linux users should take care of permissions and everyone should know that `nginx` container is **very** (production) restrictive so nothing except `index.php` will get executed.
* **docs** — all usable documentation is here
* **frontned** — is holding everything frontend related so that `docroot` only holds Drupal theme and nothing else (Sass or build files). Usually there are following directories:
  - **scss** — holding main **style.scss** and all components in their files in subdirectories
  - **images** — for **source** images that are needed in CSS (i.e. for backgrounds) that will be optimized and copied to theme.
  - **media** — for **source** media files that are used statically like slider images.
  - **js** — for **source** JS files, mostly those that we write, usually configuration and initialization.
  - **vendor** — for **source** vendor libraries whose components will be used and copied to theme.
  - **fonts** — for **source** font files that are going to be minimised, inlined and included in theme.
* **styleguide** — for more complex theme building with HTML/CSS/JS web components, **patternlab** and Style Guide Driven Development®.
* `docker-compose.yml` — standard container configuration that is used on production
* `docker-compose.local.yml` — local container configuration that configures local development
* `docker-compose.mac.yml` — local container configuration that enables **Xdebug** on Mac in local development

## Contributing

The best way to contribute is to use **pull request** mechanism, check details [here](CONTRIBUTING.md).

Those who are not comfortable with PR workflow may use [issues queue](https://gitlab.com/MacMladen/mci-drupal/issues).

## Contact

The best way to contact is to use [issues queue](https://gitlab.com/MacMladen/mci-drupal/issues).
