## Concepts

### Entry

A place for webpack to look to build out its dependency graph.

* You can have more than one
* Defaults to `./src/index.js`

```js
{
    entry: {
        app: "./src/index.js"
    }
}
```

### Output

Where webpack will put the bundles it generates.

* Can have more than one
* Defaults to `./dist/main.js` for the main bundle, and `./dist/` for any other generated files

```js
{
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    }
}
```

### Loaders

Match non-javascript files and transform them into webpack modules.

* These transform non-JS files to JS
* `test` for a particular regex match
* `use` the string name of a particular loader for it
* `exclude` for matches you don't want to include (eg. `node_modules`)

```js
{
    module: {
        rules: [{
            test: /\.txt$/,
            use: "raw-loader"
        }]
    }
}
```

### Plugins

Handle utility tasks and transformations, like optimization, environment variables, etc.

* `require`d in
* Instantiated with `new`, options passed in
* Webpack includes ~30 common plugins

```js
const HtmlWebpackPlugin = require("html-webpack-plugin"); // installed via npm
const webpack = require("webpack"); // to access built-in plugins

module.exports = {
    plugins: [
        new HtmlWebpackPlugin({
            template: "./src/index.html"
        })
    ]
};
```

### Mode

Webpack has some default optimizations it can run by setting the mode to `development`, `production`, or `none`

Development:

* Sets `NODE_ENV` to `development`
* Enables "NamedChunksPlugin" and "NamedModulesPlugin"

Production:

* Sets `NODE_ENV` to `production`
* Enables warnings on builds, disables errors, and uglifies bundles

```
{
    mode: "development"
}
```

## Examples

It's typical to have a shared webpack configuration, and then join it with dev- and prod-specific files.

### Common

```js
const path = require("path");

const CleanWebpackPlugin = require("clean-webpack-plugin");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
    entry: {
        app: "./src/index.js"
   },
    output: {
        filename: "[name].bundle.js",
        path: path.resolve(__dirname, "dist")
    },
    plugins: [
        new CleanWebpackPlugin(["dist"]),
        new HtmlWebpackPlugin({
            template: "./src/index.html"
        })
    ],
    module: {
        rules: [{
            test: /\.css$/,
            use: [
                "style-loader",
                "css-loader"
            ]
        },{
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
                loader: "babel-loader"
            }
        },{
            test: /\.(ttf|otf)$/,
            use: {
                loader: "url-loader"
            }
       },{
            test: /\.(jpg)$/,
            use: {
                loader: "file-loader"
            }
       }]
    }
};
```

### Dev

```js
const merge = require("webpack-merge");
const common = require("./webpack.common.js");
const webpack = require("webpack");

module.exports = merge(common, {
    mode: "development",
    devtool: "inline-source-map",
    devServer: {
        contentBase: "./dist",
        hot: true,
        proxy: {
            "/assets": {
                target: "",
                secure: false
            }
        }
    },
    plugins: [
        new webpack.NamedModulesPlugin(),
        new webpack.HotModuleReplacementPlugin()
    ]
});
```

### Prod

```js
const merge = require("webpack-merge");
const common = require("./webpack.common.js");
const UglifyJSPlugin = require("uglifyjs-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
const OptimizeCSSAssetsPlugin = require("optimize-css-assets-webpack-plugin");

module.exports = merge(common, {
    mode: "production",
    plugins: [
        new MiniCssExtractPlugin({
            filename: "[name].css",
            chunkFilename: "[id].css"
        })
    ],
    optimization: {
        minimizer: [
            new UglifyJSPlugin({
                cache: true,
                parallel: true,
                sourceMap: true
            }),
            new OptimizeCSSAssetsPlugin({})
        ]
    }
});
```
