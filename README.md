# grunt-toggle

> Toggles blocks within an html file depending on supplied values.

## Getting Started
This plugin requires Grunt `~0.4.2`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-toggle --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-toggle');
```

## The "toggle" task

### Overview
In your project's Gruntfile, add a section named `toggle` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  toggle: {
    dev: {
      options: {
        show: ['dev']
      }
    },
    dist: {
      options: {
        show: ['dist', 'prod']
      }
    }
  },
});
```

### Options

#### options.show
Type: `Array`
Default value: `[]`

An array of strings which correspond to the toggle comment blocks you wish to keep in your html file. All blocks not listed will be removed.

#### mode
Type: `Boolean` or `Number`
Default: `false`

Whether to copy or set the existing file permissions. Set to `true` to copy the existing file permissions. Or set to the mode, i.e.: `0644`, that copied files will be set to.

### Usage Examples

Given the following html:

```html
<html>
    <head>
        <title>toggle</title>

        <!-- toggle:head -->
        <script>console.log('head visible');</script>
        <!-- endtoggle -->
    </head>

    <body>
        <!-- toggle:body -->
        <p>body visible</p>
        <!-- endtoggle -->
    </body>
</html>
```

To only show the `head` toggle block, use the following options:

```js
grunt.initConfig({
  toggle: {
    dev: {
      options: {
        show: ['head']
      },
      files: {
        'index.html': ['index.html'],
      }
    }
  },
});
```

The output would be:

```html
<html>
    <head>
        <title>toggle</title>

        <script>console.log('head visible');</script>
    </head>

    <body>
    </body>
</html>
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
1.0.0 - Initial release
