<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# TypeScript

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

[//]: # (2. `npm i ttypescript -D`)

[//]: # (    > In order to use transformer plugin you need TypeScript compiler which supports plugins eg. package [ttypescript]&#40;https://www.npmjs.com/package/ttypescript&#41; or you can use [TypeScript compiler API]&#40;https://github.com/Microsoft/TypeScript/wiki/Using-the-Compiler-API&#41; manually.)

[//]: # (3. Now just transpile your code by `ttsc` instead of `tsc`)

[//]: # (    ```)

[//]: # (    ttsc)

[//]: # (    ```)

[//]: # (    or)

[//]: # (    ```)

[//]: # (    npx ttsc)

[//]: # (    ```)