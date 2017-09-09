# Learning Webpack

This repository is just to test out webpack

# Webpack via Command line
This is not really recommended due to variety of options available in webpack

```bash
# Using webpack from command line
# Basic usage of webpack command line
webpack ./src/app.js ./dist/app.bundle.js

# Add the production flag (Includes minifying code base)
webpack ./src/app.js ./dist/app.bundle.js -p 

# Add the prodcution and watch flag - any changes will cause rebundle
webpack ./src/app.js ./dist/app.bundle.js -p --watch
```

Create webpack.config.js instead and store the configurations there.

# Webpack configurations

Look at sample configuration markdown file

