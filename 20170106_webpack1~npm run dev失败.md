**2017.01.06**

nodejs 6.9使用webpack2+vue2，npm run dev起服务失败。
```
> vue2@ dev /Users/zhuxu/Documents/playground/vue2-router
> webpack-dev-server --open --inline --hot

/Users/zhuxu/Documents/playground/vue2-router/node_modules/webpack-dev-server/bin/webpack-dev-server.js:385
        throw e;
        ^

TypeError: webpack.validateSchema is not a function
    at new Server (/Users/zhuxu/Documents/playground/vue2-router/node_modules/webpack-dev-server/lib/Server.js:23:33)
    at startDevServer (/Users/zhuxu/Documents/playground/vue2-router/node_modules/webpack-dev-server/bin/webpack-dev-server.js:378:12)
    at /Users/zhuxu/Documents/playground/vue2-router/node_modules/webpack-dev-server/bin/webpack-dev-server.js:324:3
    at /Users/zhuxu/Documents/playground/vue2-router/node_modules/portfinder/lib/portfinder.js:160:14
    at /Users/zhuxu/Documents/playground/vue2-router/node_modules/async/lib/async.js:52:16
    at /Users/zhuxu/Documents/playground/vue2-router/node_modules/async/lib/async.js:269:32
    at /Users/zhuxu/Documents/playground/vue2-router/node_modules/async/lib/async.js:44:16
    at /Users/zhuxu/Documents/playground/vue2-router/node_modules/portfinder/lib/portfinder.js:122:16
    at Server.onListen (/Users/zhuxu/Documents/playground/vue2-router/node_modules/portfinder/lib/portfinder.js:45:7)
    at Server.g (events.js:291:16)

npm ERR! Darwin 16.3.0
npm ERR! argv "/usr/local/bin/node" "/usr/local/bin/npm" "run" "dev"
npm ERR! node v6.9.1
npm ERR! npm  v3.10.8
npm ERR! code ELIFECYCLE
npm ERR! vue2@ dev: `webpack-dev-server --open --inline --hot`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the vue2@ dev script 'webpack-dev-server --open --inline --hot'.
npm ERR! Make sure you have the latest version of node.js and npm installed.
npm ERR! If you do, this is most likely a problem with the vue2 package,
npm ERR! not with npm itself.
npm ERR! Tell the author that this fails on your system:
npm ERR!     webpack-dev-server --open --inline --hot
npm ERR! You can get information on how to open an issue for this project with:
npm ERR!     npm bugs vue2
npm ERR! Or if that isn't available, you can get their info via:
npm ERR!     npm owner ls vue2
npm ERR! There is likely additional logging output above.

npm ERR! Please include the following file with any support request:
```
网上查到如下方案
```
Looks like npm bug, since webpack-dev-server@2.1.0-beta.11
 requires webpack@^2.1.0-beta.26
but npm failed to install it.
The easiest way to avoid the issue without updating too much is to change dependency in package.json to
 "webpack-dev-server": "2.1.0-beta.10",

Instead of something like
 "webpack-dev-server": "^2.1.0-beta.9",

"^" char before version says "compatible with". Removing it sticks to the version exactly.
```