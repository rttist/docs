<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# Deno

Preparing...

[//]: # (> Because current version of Deno is based on SWC &#40;Rust&#41;, not TypeScript, there is currently no direct way to use **RTTIST**. You have to transpile TS to JS eg. via `ttypescript` and then you can run transpiled JS by `deno`.)

[//]: # ()
[//]: # (1. Install packages,)

[//]: # (    ```)

[//]: # (    npm i rttist && npm i tst-reflect-transformer -D)

[//]: # (    ```)

[//]: # (2. add transformer to `tsconfig.json`,)

[//]: # (    ```json)

[//]: # (    {)

[//]: # (        "compilerOptions": {)

[//]: # (            // your options...)

[//]: # (            "outDir": "dist",)

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

[//]: # (3. `npm i ttypescript -D`)

[//]: # (    > In order to use transformer plugin you need TypeScript compiler which supports plugins eg. package [ttypescript]&#40;https://www.npmjs.com/package/ttypescript&#41; or you can use [TypeScript compiler API]&#40;https://github.com/Microsoft/TypeScript/wiki/Using-the-Compiler-API&#41; manually.)

[//]: # (4. Transpile your code by `ttsc` instead of `tsc`)

[//]: # (    ```)

[//]: # (    ttsc)

[//]: # (    ```)

[//]: # (    or)

[//]: # (    ```)

[//]: # (    npx ttsc)

[//]: # (    ```)

[//]: # (5. `deno run dist/index.js`)