<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# ts-node

Preparing...

[//]: # (1. Install packages,)

[//]: # (    ```)

[//]: # (    npm i rttist && npm i tst-reflect-transformer -D)

[//]: # (    ```)

[//]: # (2. add transformer to `tsconfig.json` and add `ts-node` section.)

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

[//]: # (        },)

[//]: # (        )
[//]: # (        // ADD THIS!)

[//]: # (        "ts-node": {)

[//]: # (            // This can be omitted when using ts-patch)

[//]: # (            "compiler": "ttypescript")

[//]: # (        })

[//]: # (    })

[//]: # (    ```)
