## cheatsheet for inertiaJS and react with Adonis

I had some troubleshoot for isntalling react/inertia with adonis so i want to share this.

**Create your project**

```
npm init adonis-ts-app@latest my-project-name

```
**Go to directorie project**

```
cd my-project-name

```
**Install inertiaJS for adonis**

```
    npm i @eidellev/inertia-adonisjs@7.4.1

```

**Create configuration file for inertiaJS adonis**

```

    node ace configure @eidellev/inertia-adonisjs

```

**Install loader for react**


```
    npm install ts-loader @babel/preset-react --save-dev

```

**Add this lines in webpack.config.js in root project directorie**

```
    Encore.addEntry('app', './resources/js/app.js')
    Encore.enableTypeScriptLoader()
    Encore.enableReactPreset()

```

**Create tsconfig.json file in ./resources/js**

```
    {
        "include": ["**/*"],
        "compilerOptions": {
            "lib": ["DOM"],
            "jsx": "react",
            "esModuleInterop": true
        }
    }

```

**Add this lines in ./tsconfig.json**

```
    "lib": ["DOM"],
    "jsx": "react",

```

**Add this lines ./start/kernel.ts**

```
Server.middleware.register([
  () => import('@ioc:Adonis/Core/BodyParser'),
  () => import('@ioc:EidelLev/Inertia/Middleware'),
]);

```

**Install react and react dom**

```
    npm i react react-dom

```

**Add this lines in ./resources/js/app.js**

```
    import React from 'react'
import { createInertiaApp } from '@inertiajs/inertia-react'
import { createRoot } from 'react-dom/client'

createInertiaApp({
    resolve: name => require(`./Pages/${name}.tsx`),
    setup({ el, App, props }) {
        createRoot(el).render(<App {...props} />)
    },
})

```

**Update package**

```
    npm update

```

**Run your project**

```
    node ace serve --watch

```


Congrats! You can write react with inertia in Adonis GLHF
