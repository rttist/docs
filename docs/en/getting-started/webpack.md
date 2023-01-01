# Usage With Webpack

> If you use Angular or something else which has webpack encapsulated and under its own control, 
> this Usage variant may not work properly. 
> Angular has own [Usage](angular.md) description.

1. Install packages,
    ```
    npm i rttist && npm i tst-reflect-transformer -D
    ```
2. add transformer to `tsconfig.json`,
    ```json
    {
        "compilerOptions": {
            // your options...
    
            // ADD THIS!
            "plugins": [
                {
                    "transform": "tst-reflect-transformer"
                }
            ]
        }
    }
    ```
3. modify your webpack config,
    ```javascript
    const tstReflectTransform = require("tst-reflect-transformer").default;
    
    module.exports = {
        module: {
            rules: [
                {
                    test: /\.(ts|tsx)$/,
                    loader: "ts-loader",
                    options: {
                        // ADD THIS OPTION!
                        getCustomTransformers: (program) => ({
                            before: [
                                tstReflectTransform(program)
                            ]
                        })
                    }
                }
                // ... other rules
            ]
        }
        // ... other options
    };
    ```
4. `webpack` or `webpack serve`