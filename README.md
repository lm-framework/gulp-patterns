# gulp-patterns
搭建web前端自动化测试，代码分析，运行在本地或部署。其中涉及gulp如何工作，及自动化部署。
###Nodemon
> 监控 node.js 源代码的任何变化和自动重启服务器,与supervisor类似

###yargs
>yargs是一个比较轻量级的框架，它能够满足大多数命令行操作，也可以使用它的api来实现一个复杂的操作

###tsd
> tsd是搜索和安装TypeScript Definition（脚本类型定义）包的管理器，这些可以在[DefinitelyTyped][1]中找到   
TypeScript是一种可以编译成传统JavaScript的语言，它并不是完全的创造了一门新语言，而TypeScript是JavaScript语言的超集，它最大的特点就是引入了类型系统。TypeScript编译为JavaScript文件后，输出“.ts”的类型元数据信息，为我们IDE的智能感知和重构提供了重要的依据。（*.d.ts）文件可以在不需要修改原有JavaScript文件的情况下，而给JavaScript添加元数据类型信息，而这些类型信息则可以辅助IDE，给出有智能的提示信息，以及重构的依据。  
#####[用法][2]
- npm install tsd -g
- npm init //生成tsd.json文件和typing目录下生产一个tsd.d.ts文件，它会为我们引入这些模板文件，使得IDE能够识别出这样模板文件。
- tsd install jquery angular --save //安装我们需要的模板库
- tsd help //查询更多命令

###bower 
> [请看][3]

###node-inspector 
> 基于Blink开发工具的node调试器


## Quick Start
Clone this repo and run the content locally  
```bash  
	$ npm install -g node-inspector bower gulp tsd      
	$ npm install  
	$ bower install  
	$ tsd install -r -o --save  
	$ gulp serve-dev  
```

## Tasks

### Task Listing

- `gulp help`

    Displays all of the available gulp tasks.

### Code Analysis

- `gulp vet`

    Performs static code analysis on all javascript files. Runs jshint and jscs.

- `gulp vet --verbose`

    Displays all files affected and extended information about the code analysis.

- `gulp plato`

    Performs code analysis using plato on all javascript files. Plato generates a report in the reports folder.

### Testing

- `gulp serve-specs`

    Serves and browses to the spec runner html page and runs the unit tests in it. Injects any changes on the fly and re runs the tests. Quick and easy view of tests as an alternative to terminal via `gulp test`.

- `gulp test`

    Runs all unit tests using karma runner, mocha, chai and sinon with phantomjs. Depends on vet task, for code analysis.

- `gulp test --startServers`

    Runs all unit tests and midway tests. Cranks up a second node process to run a server for the midway tests to hit a web api.

- `gulp autotest`

    Runs a watch to run all unit tests.

- `gulp autotest --startServers`

    Runs a watch to run all unit tests and midway tests. Cranks up a second node process to run a server for the midway tests to hit a web api.

### Cleaning Up

- `gulp clean`

    Remove all files from the build and temp folders

- `gulp clean-images`

    Remove all images from the build folder

- `gulp clean-code`

    Remove all javascript and html from the build folder

- `gulp clean-fonts`

    Remove all fonts from the build folder

- `gulp clean-styles`

    Remove all styles from the build folder

### Fonts and Images

- `gulp fonts`

    Copy all fonts from source to the build folder

- `gulp images`

    Copy all images from source to the build folder

### Styles

- `gulp styles`

    Compile less files to CSS, add vendor prefixes, and copy to the build folder

### Bower Files

- `gulp wiredep`

    Looks up all bower components' main files and JavaScript source code, then adds them to the `index.html`.

    The `.bowerrc` file also runs this as a postinstall task whenever `bower install` is run.

### Angular HTML Templates

- `gulp templatecache`

    Create an Angular module that adds all HTML templates to Angular's $templateCache. This pre-fetches all HTML templates saving XHR calls for the HTML.

- `gulp templatecache --verbose`

    Displays all files affected by the task.

### Serving Development Code

- `gulp serve-dev`

    Serves the development code and launches it in a browser. The goal of building for development is to do it as fast as possible, to keep development moving efficiently. This task serves all code from the source folders and compiles less to css in a temp folder.

- `gulp serve-dev --nosync`

    Serves the development code without launching the browser.

- `gulp serve-dev --debug`

    Launch debugger with node-inspector.

- `gulp serve-dev --debug-brk`

    Launch debugger and break on 1st line with node-inspector.

- `gulp serve-dev --stubs`

    Serves the development code with the stubs to avoid hitting a real backend

### Building Production Code

- `gulp optimize`

    Optimize all javascript and styles, move to a build folder, and inject them into the new index.html

- `gulp build`

    Copies all fonts, copies images and runs `gulp optimize` to build the production code to the build folder.

### Serving Production Code

- `gulp serve-build`

    Serve the optimized code from the build folder and launch it in a browser.

- `gulp serve-build --nosync`

    Serve the optimized code from the build folder and manually launch the browser.

- `gulp serve-build --debug`

    Launch debugger with node-inspector.

- `gulp serve-build --debug-brk`

    Launch debugger and break on 1st line with node-inspector.
[1]: https://github.com/DefinitelyTyped/DefinitelyTyped
[2]: https://github.com/Definitelytyped/tsd#readme
[3]: https://github.com/lm-utils/bower