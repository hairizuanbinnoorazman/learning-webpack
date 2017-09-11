**Simple Configurations**

```js
module.exports = {
    entry: './src/app.js',
    output: {
        filename: './dist/app.bundle.js'
    }
}
```

**With HTML Configuration**
Interesting thing to note: path in output only takes in absolute path.
Hence, that is why u need to define variables to retreive the name of the folder where the webpack config file is.

Use the `__dirname` to get the Current directory name.

This file generates the index.html file (see the options available)

Also, as an additional bonus, we can minify the html (removes white space) as well as hash the javascript (this is to invalidate cache).

```js
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    entry: './src/app.js',
    output: {
        path: __dirname + '/dist',
        filename: 'app.bundle.js'
    },
    plugins: [new HtmlWebpackPlugin({
        title: 'Project Demo',
        minify: {
            collapseWhitespace: true
        },
        hash: true,
        template: './src/index.ejs'}
    )]
}
```


**With css loaders**

For modules, the module rules are read from right to left
e.g. sass-loader read into css-loader then into style-loader

```js
var HtmlWebpackPlugin = require('html-webpack-plugin');
var ExtractTextPlugin = require('extract-text-webpack-plugin');

module.exports = {
    entry: './src/app.js',
    output: {
        path: __dirname + '/dist',
        filename: 'app.bundle.js'
    },
    module: {
        rules: [
            {
                test: /\.scss$/,
                use: ExtractTextPlugin.extract({
                    fallback: "style-loader",
                    use: ['css-loader', 'sass-loader'],
                    publicPath: '/dist'
                })
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
            title: 'Project Demo',
            minify: {
                collapseWhitespace: true
            },
            hash: true,
            template: './src/index.ejs'}),
        new ExtractTextPlugin({
            filename: "app.css",
            disable: false,
            allChunks: true})
    ]
}
```