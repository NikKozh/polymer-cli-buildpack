# polymer-cli-buildpack

A buildpack to support Heroku deployments with [polymer-cli](https://github.com/Polymer/tools/tree/master/packages/cli).

## Installation

#### Heroku Dashboard

Add a custom buildpack to your to your applications Settings tab under
section Buildpacks by using the URL of this repository, instead of the
short name of Heroku's own buildpacks. It goes alongside your Ruby and
Node buildpacks, placed in last position.

After the release of registered buildpacks, it will be available under
the name `lingolive/polymer-cli-buildpack`, adhearing to the suggested naming
conventions there.

#### Heroku CLI

First, check your Heroku app has the Ruby and Node buildpacks added, in the command line run:

    heroku buildpacks

If they are added you should see:

    your-app-1234 Buildpack
    1. heroku/nodejs
    2. heroku/ruby

To add the Polymer CLI Rails buildpack in the last index, run this command:

    heroku buildpacks:add --index 3 https://github.com/lingolive/polymer-cli-buildpack.git

## Usage

On deployment, the buildpack runs the build command `polymer build` or `yarn build`.

### Package Manager

Heroku supports both NPM and Yarn as Javascript package managers. This buildpack will
detect which one to use automatically, based on the persence of a version-lock file.
Projects that use yarn have
a `yarn.lock` file, while those that use npm have a `package-lock.json`
(or none if using an older version of `npm`).

This buildpack will set the `YARN` environment variable accordingly, which
will make that the effective package manager for Javascript.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

Forked from https://github.com/febeling/webpack-rails-buildpack on August 18, 2018.

## Credits

polymer-cli-buildpack built and maintained by Lingo Live
https://github.com/febeling/webpack-rails-buildpack by Florian Ebeling.

## License

See LICENSE.md file.
