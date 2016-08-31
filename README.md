# gulp-github-release

Create GitHub releases and upload assets.

## Installation

```
npm install --save-dev gulp-github-release
```

## Usage

```js
var release = require('gulp-github-release');

gulp.task('release', function(){
  gulp.src('./dist/some-file.exe')
    .pipe(release({
      token: 'token',                     // or you can set an env var called GITHUB_TOKEN instead
      owner: 'remixz',                    // if missing, it will be extracted from manifest (the repository.url field)
      repo: 'publish-release',            // if missing, it will be extracted from manifest (the repository.url field)
      tag: 'v1.0.0',                      // if missing, the version will be extracted from manifest and prepended by a 'v'
      name: 'publish-release v1.0.0',     // if missing, it will be the same as the tag
      notes: 'very good!',                // if missing it will be left undefined
      draft: false,                       // if missing it's false
      prerelease: false,                  // if missing it's false
      manifest: require('./package.json') // package.json from which default values will be extracted if they're missing
    }));
});
```

If it doesn't work and you get something along these lines:

```
[18:18:15] Release created successfully at https://github.com/suited/suited.js/releases/tag/1.0.11-alpha+bd.2016-8-31-181759-000.commitish.c86dd46a4d383ae3083df01a38d2b99fee2f0382 events.js:87 throw Error('Uncaught, unspecified "error" event.'); ^ Error: Uncaught, unspecified "error" event. at Error (native) at DestroyableTransform.emit (events.js:87:13) at done (/home/robertk/projects-oss/suited.js/node_modules/through2/node_modules/readable-stream/lib/_stream_transform.js:168:25) at /home/robertk/projects-oss/suited.js/node_modules/through2/node_modules/readable-...
```

Please see https://github.com/Aluxian/gulp-github-release/issues/3

## License

The MIT License (MIT)

Copyright (c) 2015 Alexandru Rosianu

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
