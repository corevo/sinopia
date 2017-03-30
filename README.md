`sinopia-apm` - a private/caching npm repository server for atom packages

This fork is used to host private atom packages, or to use apm behind a firewall.

## About this fork
This is a fork of @fl4re sinopia, to allow scoped packages as well, works with `apm-server` as a proxy for atom.
You will still need another sinopia, or another way of caching npm, even using npmjs.org to store npm packages, since some atom packages have the same name as other npm packages.
e.g. [react](https://github.com/facebook/react) and [atom-react](https://github.com/orktes/atom-react) have the same name in their `package.json` and need to be stored in different sinopias, you would store `atom-react` here, while storing react in any other means.

## Use cases

1. Use private atom packages.

   If you have atom packages that are meant to be used privately you may use this as a way to host the private package.

2. Cache atom.io registry.

   If you are behind a firewall and can't install packages directly from atom.io, you can use this to cache those.

3. Override public packages.

   If you want to override public atom packages, you can use this to store the overriden package.

## Installation

```bash
# installation and starting (application will create default
# config in config.yaml you can edit later)
$ npm install -g sinopia-apm
$ sinopia

# npm configuration
$ npm set registry http://localhost:4873/

# if you use HTTPS, add an appropriate CA information
# ("null" means get CA list from OS)
$ npm set ca null
```

Now you can navigate to [http://localhost:4873/](http://localhost:4873/) where your local packages will be listed and can be searched.

### Docker

A Sinopia docker image [is available](https://registry.hub.docker.com/u/keyvanfatehi/sinopia/)

### Chef

A Sinopia Chef cookbook [is available at Opscode community](http://community.opscode.com/cookbooks/sinopia) source: https://github.com/BarthV/sinopia-cookbook

### Puppet

A Sinopia puppet module [is available at puppet forge](http://forge.puppetlabs.com/saheba/sinopia) source: https://github.com/saheba/puppet-sinopia

## Configuration

When you start a server, it auto-creates a config file.

## Adding a new user

```bash
npm adduser --registry http://localhost:4873/
```

This will prompt you for user credentials which will be saved on the Sinopia server.

## Storage

No CouchDB here. This application is supposed to work with zero configuration, so filesystem is used as a storage.

If you want to use a database instead, ask for it, we'll come up with some kind of a plugin system.
