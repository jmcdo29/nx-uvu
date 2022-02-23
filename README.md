# nx-uvu

An Nx executor for the uvu test runner!

## Installation

Just your standard install.

```sh
npm i -D nx-uvu
pnpm i -D nx-uvu
yarn add --dev nx-uvu
```

## Usage

Set your executor to `nx-uvu:uvu` like so:

```json
{
  "project": {
    "root": "path/to/project",
    "type": "type",
    "sourceRoot": "path/to/project/src",
    "targets": {
      "test": {
        "executor": "nx-uvu:uvu",
        "options": {
          "rootDir": "./packages/styler/test",
          "coverage": true,
          "coverageConfig": "./packages/styler/.c8rc",
          "useSwc": true
        }
      }
    }
  }
}
```

And now `nx run test project` will use the `uvu` executor!

<!-- prettier-ignore-start -->
## Options

There's some configuration options you can make use of with this executor to help really boost your tests speeds.

| Option | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| rootDir | string | null | true | The root directory to run the uvu command from. |
| pattern | string | "(test\|spec)\\.(j\|t)" | false | The test pattern to pass to the uvu CLI |
| coverage | boolean | false | false | Whether or not c8 should be used to collect coverage. Keep this false if you'd rather use `nyc` or your own coverage collector |
| coverageConfig | string | null | false | The path to the c8 config file |
| typescript | boolean | true | false | If you'd like to use typescript files for your tests. This will automatically use `ts-node` |
| useSwc | boolean | false | false | Use SWC instead of ts-node and tsconfig-paths |
| tsconfigPaths | boolean | true | false | If tsconfig-paths should be registered. THis will only be registered if "typescript" is `true` and "useSwc" is `false` | [] | false | Any other arguments you want to pass to the `-r` hook |
| color | boolean | true | false | If colors should be used with the test output |
<!-- prettier-ignore-end -->

## Contributing and Contacting

If I left something out, or we can make this better somehow, open an issue or a pull request! I'll be happy to take a look and see what we can do.
