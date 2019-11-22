# amdefine

Can turn the resource path of HTM \ HTML file or background:url('xxxx') into an absolute path, and add the CDN prefix

## Install

```javascript
npm install gulp-htm-path --save-dev
```

## Usage && API

```javascript
const htmlPath = require('gulp-htm-path');
gulp.task('build_html', function() {
    return gulp.src(['**/*.{htm,html}'])
        .pipe(htmlPath({
            //root path
            base: './src',
            //mode: 'relative' or 'absolute'
            mode: 'absolute',
            //prefix url
            prePath: '//image.xxx.com/static/dist',
            //print log
            log: false,
            //ignore: URL include "#ignore" will not be replaced
            ignore:'#ignore'
        }))
        .pipe(gulp.dest('./dist'));
});
```
## example
**1)** html
```html
<!DOCTYPE html>
<html>

<head>
    <title>test</title>
    <meta http-equiv="content-type" content="text/html;charset=utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    <link rel="stylesheet" type="text/css" href="./css/style.css" />
    <link rel="stylesheet" type="text/css" href="/page/help/css/style.css?inline" inline />
</head>

<body>
    <div>test</div>
    <img src="./img/welfareicon.png" />
    <img src="/page/help/img/welfareicon.png?inline" inline />
    <img src="/page/help/img/welfareicon.png" />
    <img src="./img/welfareicon.png" />
    <script src="/page/help/js/main.js?inline" inline></script>
    <script src="./../help/js/main.js"></script>
    <script src="../../page/help/js/main.js"></script>
    <script src="js/main.js"></script>
    <script src="/page/help/js/main.js"></script>
</body>

</html>
```
**2)** convert after

```html
<!DOCTYPE html>
<html>

<head>
    <title>test</title>
    <meta http-equiv="content-type" content="text/html;charset=utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    <link rel="stylesheet" type="text/css" href="//image.xxx.com/static/dist/page/help/css/style.css" />
    <link rel="stylesheet" type="text/css" href="/page/help/css/style.css?inline" inline />
</head>

<body>
    <div>test</div>
    <img src="//image.xxx.com/static/dist/page/help/img/welfareicon.png" />
    <img src="${staticPath}/page/index/img/welfareicon.png" />
    <img src="/page/help/img/welfareicon.png?inline" inline />
    <img src="//image.xxx.com/static/dist/page/help/img/welfareicon.png" />
    <img src="//image.xxx.com/static/dist/page/help/img/welfareicon.png" />
    <script src="/page/help/js/main.js?inline" inline></script>
    <script src="//image.xxx.com/static/dist/page/help/js/main.js"></script>
    <script src="//image.xxx.com/static/dist/page/help/js/main.js"></script>
    <script src="//image.xxx.com/static/dist/page/help/js/main.js"></script>
    <script src="//image.xxx.com/static/dist/page/help/js/main.js"></script>
</body>

</html>
```

## License

New BSD and MIT. Check the LICENSE file for all the details.
