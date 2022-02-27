# Vue 3 + Typescript + Vite

This template should help get you started developing with Vue 3 and Typescript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## How this project was created?
You can use this command to create a project like this:
```bash
npm init vite@latest my-app -- --template vue-ts
cd my-app
npm install
```

## Recommended IDE Setup

- [VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

## Type Support For `.vue` Imports in TS

Since TypeScript cannot handle type information for `.vue` imports, they are shimmed to be a generic Vue component type by default. In most cases this is fine if you don't really care about component prop types outside of templates. However, if you wish to get actual prop types in `.vue` imports (for example to get props validation when using manual `h(...)` calls), you can enable Volar's `.vue` type support plugin by running `Volar: Switch TS Plugin on/off` from VSCode command palette.

## Type inference
The type inference is possible using TypeScript and Vue3, the `setup` attribute in the `<script>` tag allows you to write a TypeScript code, here is an example:
```html
<script setup lang="ts">
import { ref, reactive } from 'vue'

interface User {
    username: string;
    age: number;
}
const count = ref(0)
const user: User = reactive({
    username: 'Admin',
    age: 36
})
</script>

<template>
  <h1>Welcome {{ user.username }}!</h1>
  <p>You are {{ user.age }} years old.</p>
  <span>Counter: {{ count }}</span>
</template>
```

## Adding unit testing
Read more at: https://dev.to/vuesomedev/add-testing-to-vite-4b75

## Testing (not implemented yet)
Use [Vitest](https://vitest.dev/) for testing:
```
npm install -D vitest
```