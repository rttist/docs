<script>
setPagination(
    "/en/getting-started/installation",
    "/en/getting-started/setup"
);
</script>

# Angular
> Because Angular CLI does not support custom TypeScript transformers/plugins (there is still an open [feature request](https://github.com/angular/angular/issues/22434), more than 4 years), custom transformers must be configured manually by tampering with the Webpack configuration file.

Preparing...

[//]: # (For this purpose the [ng-custom-transformers]&#40;https://www.npmjs.com/package/ng-custom-transformers&#41; )

[//]: # (package was created which simplifies the usage.)

[//]: # ()
[//]: # (> Because this solution is not "native" there can be some problems with some Angular's utilities, eg. packgr.)

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

[//]: # (3. `npm i ng-custom-transformers -D`,)

[//]: # (4. continue by [A]&#40;#a-angular-builderscustom-webpack&#41; or [B]&#40;#b-ngx-build-plus&#41;.)

[//]: # ()
[//]: # ()
[//]: # (## A. @angular-builders/custom-webpack)

[//]: # (5. `npm i @angular-builders/custom-webpack -D`,)

[//]: # (6. create file `mod.webpack.config.js`,)

[//]: # (    ```javascript)

[//]: # (    const {AngularCustomTransformers} = require&#40;"ng-custom-transformers"&#41;;)

[//]: # (    )
[//]: # (    module.exports = &#40;config, options, targetOptions&#41; => {)

[//]: # (        // Your transformations of "config" ....)

[//]: # (    )
[//]: # (        // And the important part here: modifyConfig&#40;&#41;)

[//]: # (        return AngularCustomTransformers.modifyConfig&#40;config&#41;;)

[//]: # (    };)

[//]: # (    ```)

[//]: # (7. modify `angular.json`,)

[//]: # (    ```json)

[//]: # (    {)

[//]: # (        "architect": {)

[//]: # (            // ...)

[//]: # (            "build": {)

[//]: # (                "builder": "@angular-builders/custom-webpack:browser",)

[//]: # (                // use @angular-builders/custom-webpack builder)

[//]: # (                "options": {)

[//]: # (                    "customWebpackConfig": {)

[//]: # (                        "path": "./mod.webpack.config.js")

[//]: # (                    })

[//]: # (                    // ...)

[//]: # (                })

[//]: # (            },)

[//]: # (            "serve": {)

[//]: # (                "builder": "@angular-builders/custom-webpack:dev-server",)

[//]: # (                // use @angular-builders/custom-webpack builder)

[//]: # (                // ...)

[//]: # (            },)

[//]: # (        })

[//]: # (    })

[//]: # (    ```)

[//]: # (8. `ng build` or `ng serve` done.)

[//]: # ()
[//]: # (## B. ngx-build-plus)

[//]: # (5. `ng add ngx-build-plus`)

[//]: # (6. `ng build --plugin ng-custom-transformers` or `ng serve --plugin ng-custom-transformers`)

[//]: # ()
[//]: # (    > `ngx-build-plus` overrides `angular.json` automatically.)

[//]: # ()
[//]: # ()
[//]: # (## Demo)

[//]: # (Demo project on StackBlitz [here]&#40;https://stackblitz.com/edit/tst-reflect-angular-ag-custom-transformers?file=src%2Fapp%2Fapp.component.ts&#41;.)