<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# Webpack

> If you use Angular or something else which has webpack encapsulated and under its own control, 
> this Usage variant may not work properly. 
> Angular has own [Installation](angular.md) description.

Preparing...

[//]: # (1. Install packages,)

[//]: # (    ```)

[//]: # (    npm i rttist && npm i tst-reflect-transformer -D)

[//]: # (    ```)

[//]: # (2. add transformer to `tsconfig.json`,)

[//]: # (    ```json)

[//]: # (    {)

[//]: # (        "compilerOptions": {)

[//]: # (            // your options...)

[//]: # (    )
[//]: # (            // ADD THIS!)

[//]: # (            "plugins": [)

[//]: # (                {)

[//]: # (                    "transform": "tst-reflect-transformer")

[//]: # (                })

[//]: # (            ])

[//]: # (        })

[//]: # (    })

[//]: # (    ```)

[//]: # (3. modify your webpack config,)

[//]: # (    ```javascript)

[//]: # (    const tstReflectTransform = require&#40;"tst-reflect-transformer"&#41;.default;)

[//]: # (    )
[//]: # (    module.exports = {)

[//]: # (        module: {)

[//]: # (            rules: [)

[//]: # (                {)

[//]: # (                    test: /\.&#40;ts|tsx&#41;$/,)

[//]: # (                    loader: "ts-loader",)

[//]: # (                    options: {)

[//]: # (                        // ADD THIS OPTION!)

[//]: # (                        getCustomTransformers: &#40;program&#41; => &#40;{)

[//]: # (                            before: [)

[//]: # (                                tstReflectTransform&#40;program&#41;)

[//]: # (                            ])

[//]: # (                        }&#41;)

[//]: # (                    })

[//]: # (                })

[//]: # (                // ... other rules)

[//]: # (            ])

[//]: # (        })

[//]: # (        // ... other options)

[//]: # (    };)

[//]: # (    ```)

[//]: # (4. `webpack` or `webpack serve`)