# compass-serverstats [![][travis_img]][travis_url] [![][npm_img]][npm_url]

> Compass Real Time Server Stats Component.

## Installation

In the `package.json`:

```json
  "dependencies": {
    "compass-serverstats": "10gen/compass-serverstats",
  }
```

## Usage

```js
const d3 = require('d3');
const realTimeLineChart = require('compass-serverstats').d3.realTimeLineChart;

const el = document.getElementById('myChart');
const data = {
  "dataSets" : [
    {
      "line" : "virtual",
      "count" : [
        2.48,
        2.48,
        2.49
      ],
      "active" : true
    },
    {
      "line" : "resident",
      "count" : [
        0.02,
        0.02,
        0.02
      ],
      "active":true
    },
    {
      "line" : "mapped",
      "count" : [
        0,
        0,
        0
      ],
      "active":true
    }
  ],
  "localTime" : [
    "2016-10-30T07:12:05.077Z",
    "2016-10-30T07:12:06.069Z",
    "2016-10-30T07:12:07.153Z"
  ],
  "skip" : [
    false,
    false,
    false
  ],
  "yDomain" : [
    0,
    2.49
  ],
  "xLength" : 60,
  "labels" : {
    "title" : "memory",
    "keys" : [
      "vsize",
      "resident",
      "mapped"
    ],
    "yAxis" : "GB"
  },
  "keyLength" : 6,
  "paused" : false
};

d3.select(el).datum(data).call(realTimeLineChart());
```

## Features

#### Storybook

Develop and prototype your component with [react-storybook][react-storybook] in a standalone browser view, with linked stories and hot reloading.

To run storybook mode, type `npm run storybook`, then open
[http://localhost:9001](http://localhost:9001) in a browser. You can now edit the source code and hit _save_, and changes will immediately show in the browser, while maintaining the state of the component(s).

#### Electron

Validate and test your component in an Electron window, styles included. The source automatically compiles and the window content reloads when any file under `./src` changes.

To start Electron and render your component, type `npm start`.

If you edit the source code and hit _save_, the source will rebuild and the window reload automatically. State is not maintained throughout reloads (to maintain application state, use _storybook_ instead).

#### Enzyme

The test environment is configured to test components with [Enzyme][enzyme] (including full `mount` mode through [jsdom][jsdom]) and [enzyme-chai][enzyme-chai]. See the test folder for examples. Run `npm test` to execute the test suite.

## Developing

Almost all of your development will happen in the `./src` directory. Add new components
to `./src/components`, actions to `./src/actions/index.js` and if you need additional stores, add them to `./src/stores`.

#### Directory Structure

For completeness, below is a list of directories present in this module:

- `.storybook` react-storybook and webpack configuration. You usually don't need to touch this.
- `electron` code to start electron, open a browser window and load the source. You don't usually need to touch this, unless you want to render something other than the main component in Electron.
- `lib` compiled version of your components (plain javascript instead of `jsx`) and styles (`css` instead of `less`). Never change anything here as this entire folder gets automatically created and overwritten.
- `src` components, actions and stores source code, as well as style files. This is the place to implement your own components. `npm run compile` will use `./src` as input and create `./lib`.
- `stories` stories for react-storybook. You can add as many story files as you like, they are automatically added to storybook.
- `test` implement your tests here, and name the files `*.test.js`.


## License

Apache 2.0

[travis_img]: https://api.travis-ci.com/10gen/compass-serverstats.svg?token=q2zsnxCbboarF6KYRYxM&branch=master
[travis_url]: https://travis-ci.com/10gen/compass-serverstats
[npm_img]: https://img.shields.io/npm/v/mongodb-component-template.svg?style=flat-square
[npm_url]: https://www.npmjs.org/package/mongodb-component-template
[react-storybook]: https://github.com/kadirahq/react-storybook
[enzyme]: http://airbnb.io/enzyme/
[enzyme-chai]: https://github.com/producthunt/chai-enzyme
[jsdom]: https://github.com/tmpvar/jsdom
