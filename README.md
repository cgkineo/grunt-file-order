# grunt-file-order

A grunt extension for order files after selection.  
Adds ```order``` attribute to both config [``files``](https://gruntjs.com/configuring-tasks#files) array objects and [``grunt.file.expand``](https://gruntjs.com/api/grunt.file#grunt.file.expand).

### Installation
```js
$ npm install --save grunt-file-order
```
### Usage
#### In config
```js
require('grunt-file-order'); // global addition to grunt
module.exports = function (grunt, options) {
  return {
    copyFiles: {
      files: [
        {
          expand: true,
          src: ['<%= sourcedir %>**'],
          dest: '<%= outputdir %>',
          order: function(filepaths) {
            // sort alphabetically
            return filepaths.sort(function(a,b) {
              return a>b ? 1 : a<b ? -1 : 0;
            });
          }
        }
      ]
    }
  };
};
```

#### In task
```js
require('grunt-file-order'); // global addition to grunt

var sourcedir = "./src";
var files = grunt.file.expand({ 
  order: function(filepaths) {
    // sort alphabetically
    return filepaths.sort(function(a,b) {
      return a>b ? 1 : a<b ? -1 : 0;
    });
  }
}, sourcedir);
```
