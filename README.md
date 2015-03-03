# grunt-htmlhint-inline

> Grunt task for linting inline html

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-htmlhint-inline --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-htmlhint-inline');
```

## The "htmlhint-inline" task

### Overview
In your project's Gruntfile, add a section named `htmlhint-inline` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  htmlhint_inline: {
      options: {
        htmlhintrc: '.htmlhintrc',
        ignore: {
            '<?php': '?>'
        }
      },
      dest: {
        src: ['./test/*.phtml']
      }
    },
});
```

### Options

#### htmlhintrc
Type: String Default value: null

```htmlhintrc``` file must be a valid JSON.
If you specify this file, options that have been defined in it will be used in the global.
If there is specified in the task options, the options in this file will be overwritten.

```json
{
  "tagname-lowercase": true
}
```

#### patterns
Type: Array Default: []

Enable the replacement by the pattern

##### patterns.match

Type: RegExp|String

Indicates the matching expression.

##### patterns.replacement

Type: String|Function

#### reporterOutput

Type: String  Default: null

Output the task execution results to a specified file.

#### force

Type: Boolean Default value: false

Report HTMLHint errors but dont fail the task


### Usage Examples

#### Default Options
In this example, the default options are used to do something with whatever. So if the `testing` file has the content `Testing` and the `123` file had the content `1 2 3`, the generated result would be `Testing, 1 2 3.`

```js
grunt.initConfig({
  htmlhint_inline: {
      options: {
        "tagname-lowercase": true,
        "attr-lowercase": true,
        ignore: {
            '<?php': '?>'
        }
      },
      dest: {
        src: ['./test/*.phtml']
      }
    },
});
```

#### Custom Options
In this example, custom options are used to do something else with whatever else. So if the `testing` file has the content `Testing` and the `123` file had the content `1 2 3`, the generated result in this case would be `Testing: 1 2 3 !!!`

```js
grunt.initConfig({
    htmlhint_inline: {
      options: {
        htmlhintrc: '.htmlhintrc',
        ignore: {
            '<?php': '?>'
        },
        patterns: [
          {
            match: /hoge/g,
            replacement: 'fuga'
          }
        ],
        reporterOutput: './log/grunt.log',
      },
      dest: {
        src: ['./test/*.phtml']
      }
    }
});
```
## License

MIT
