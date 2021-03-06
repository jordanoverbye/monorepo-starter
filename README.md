# Monorepo Starter

> An example setup of how to do a monorepo, used in our [monorepo getting started guide]()
> Usable as a template from github

## Using this Starter

1. Clone this repository, or click the `use this template` button on github.
2. Delete packages you do not need, and add your own packages in the folder that makes most sense.
3. run `yarn`

You are now ready to start developing within the monorepo!

If you are interested in how to further configure your project, or want more information on why it is set up like this, check out our [monorepo style guide](https://github.com/Thinkmill/monorepo)

## What is included in this starter

### Packages set up

We have set up three different folders to put packages, based on their needs, each of which can include new packages. Here is the base structure:

```
- packages/
    - simple-package
    - with-multi-entrypoints
    - private-package
- apps/
    - placeholder-app
- websites/
    - placeholder-website
```

To determine where to place a new package:

- If it is designed to be consumed by other packages, and not run on its own, put it in the `/packages` folder. These may be published to npm, but can also include private packages.
- If it is a node app to be deployed, put it in the `/apps` folder
- If it a website to be deployed, put it in the `/websites` folder

> We recommend deleting any of these folders that you don't intend to use in your project

### Tools set up

- [yarn workspaces](https://legacy.yarnpkg.com/en/docs/workspaces/)
- [preconstruct](https://preconstruct.tools/)
- [manypkg](https://github.com/thinkmill/manypkg)
- [changesets](https://github.com/changesets/changesets)
- [babel](https://babeljs.io/)
- [jest](https://jestjs.io/)

Each of these tools has configuration specific to its usage in a monorepo which we have configured for you. See our [style guide](https://github.com/Thinkmill/monorepo) for more information on the configuration for each tool.

If you plan to use any of the following, please see the style guide for how to set them up:

- next
- gatsby
- typescript

### workflows set up

- install: run `yarn`
  - This also runs a `postinstall` hook that will validate your monorepo setup (using `manykpkg`), and set your packages up for dev (using `preconstruct`)
- test: run `yarn test`, which will run jest tests.
- build: run `yarn build`
  - This uses preconstruct to build `dist` files from the source of all packages in `/packages` and `/apps`. You will need to add your own build scripts if you need to build websites.
- release: run `yarn release`
  - this will run the build command, and then run `changeset publish`

We strongly recommend using changesets for versioning as well. [Here is a base explanation of the workflow](https://github.com/atlassian/changesets/blob/master/docs/intro-to-using-changesets.md)
