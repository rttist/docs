<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# Rollup

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

[//]: # (3. install Rollup plugin `npm i rollup-plugin-typescript2`,)

[//]: # (4. modify your rollup config.)

[//]: # (    ```javascript)

[//]: # (    import ttypescript from "ttypescript";)

[//]: # (    import tsPlugin from "rollup-plugin-typescript2";)

[//]: # (    )
[//]: # (    export default {)

[//]: # (        // your options...)

[//]: # (        )
[//]: # (        plugins: [)

[//]: # (            // ADD THIS!)

[//]: # (            tsPlugin&#40;{)

[//]: # (                typescript: ttypescript)

[//]: # (            }&#41;)

[//]: # (        ])

[//]: # (    })

[//]: # (    ```)