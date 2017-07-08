## Getting Started

* To create an addon: `ember addon <name>`

## Important Directories

* `/addon`- “private area”, own namespace
* `/app`- will get merged
* `/tests/dummy`- dummy application to test your component

## Important Files

* `Brocfile.js` - only gets used by the dummy application
* `index.js`
    * Entry point for the addon
    * `included` hook runs during `ember build`
    * Can `app.import` third-party dependencies and assets
    * `isDevelopingAddon: true` ← enables `liveReload`
* `package.json`
    * `ember-addon` hash includes:
        * `configPath`
        * `before`/`after` hooks for other addons
        * `demoURL` for fully qualified demo site URL
* `blueprints/<name>/index.js`
    * Runs after installation
    * Can use `contentFor` to add a content helper

## Publishing

* Need to fill out `package.json`
* Need a property in `package.json` with `"package-name": "npm-version"`
* `npm link` in addon to locally publish, `npm install ../<path>` to locally install
    * Have to manually run blueprint with `ember g <blueprint-name>`
* `npm publish` to publically publish

## Notes

* Import/export your addon in the app folder to make it available
* Templates go in the app area
* Don’t use stylesheets for addons, or give them their own addons
* You can include dependencies like normal in an addon
* Don’t use prototype extensions in an addon
* You can `.npmignore` tests and dependencies
* `LiveReload` is disabled by default. Enable in `index.js`
* Addons can install bower packages
* A linked local addon can livereload in your app
