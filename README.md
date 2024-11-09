# Nuxt ShadcnVue Error Reproduction

This is a reproduction of the error I'm facing with Nuxt and ShadcnVue, it seems that the `shadcn-vue` package is not working properly with Nuxt and bun. The error varies depending on the configuration:

It can be either:

```sh
ℹ Installing shadcn-nuxt@latest dependency                                                                                3:12:29 p.m.
bun add v1.1.33 (247456b6)

$ nuxt prepare
✔ Types generated in .nuxt                                                                                                3:12:30 p.m.

installed shadcn-nuxt@0.11.2

2 packages installed [1077.00ms]
ℹ Adding shadcn-nuxt to the modules                                                                                       3:12:30 p.m.

 ERROR  Nuxt module should be a function: @nuxtjs/tailwindcss                                                              3:12:31 p.m.

  at loadNuxtModuleInstance (node_modules/@nuxt/kit/dist/index.mjs:2460:11)
  at async installModule (node_modules/@nuxt/kit/dist/index.mjs:2389:47)
  at async setup (node_modules/shadcn-nuxt/dist/module.mjs:45:5)
  at async normalizedModule (node_modules/@nuxt/kit/dist/index.mjs:2140:17)
  at async installModule (node_modules/@nuxt/kit/dist/index.mjs:2397:95)
  at async initNuxt (node_modules/nuxt/dist/index.mjs:4669:5)
  at async loadNuxt (node_modules/nuxt/dist/index.mjs:4839:5)
  at async loadNuxt (node_modules/@nuxt/kit/dist/index.mjs:2627:19)
  at async Object.run (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/chunks/prepare.mjs:61:18)
  at async runCommand$1 (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:1648:16)
  at async runCommand (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:2019:10)
  at async Object.setup (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/chunks/add2.mjs:197:5)
  at async runCommand$1 (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:1620:5)
  at async runCommand$1 (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:1639:11)
  at async runCommand$1 (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:1639:11)
  at async runMain$1 (/home/cuervolu/.npm/_npx/b95349761371180e/node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:1777:7)



 ERROR  Nuxt module should be a function: @nuxtjs/tailwindcss                                                              3:12:31 p.m.
```

Or:

```sh
bunx shadcn-vue@latest init
✔ Would you like to use TypeScript? (recommended)? … no / yes
✔ Which framework are you using? › Nuxt
✔ Which style would you like to use? › New York
✔ Which color would you like to use as base color? › Zinc
✔ Where is your tsconfig.json file? … .nuxt/tsconfig.json
✔ Where is your global CSS file? (this file will be overwritten) … src/assets/main.css
✔ Would you like to use CSS variables for colors? … no / yes
✔ Are you using a custom tailwind prefix eg. tw-? (Leave blank if not) …
✔ Where is your tailwind.config located? (this file will be overwritten) … tailwind.config.ts
✔ Configure the import alias for components: … @/components
✔ Configure the import alias for utils: … @/utils
✔ Write configuration to components.json. Proceed? … yes
                                                                                                                                              
✔ Writing components.json...
⠋ Initializing project...                                                                                                                                              
ℹ Detected a Nuxt project with 'shadcn-nuxt' v0.11.2...                                                                                      
✔ Initializing project...
⠦ Installing dependencies...
 ERROR  Command failed with exit code 1: bun add tailwindcss-animate class-variance-authority clsx tailwind-merge radix-vue @radix-icons/vue  2:31:58 PM
Resolving dependencies
Resolved, downloaded and extracted [23]
Saved lockfile

$ nuxt prepare

 ERROR  Nuxt module should be a function: @nuxtjs/color-mode

  at loadNuxtModuleInstance (node_modules/@nuxt/kit/dist/index.mjs:2460:11)
  at async installModule (node_modules/@nuxt/kit/dist/index.mjs:2389:47)
  at async setup (node_modules/shadcn-nuxt/dist/module.mjs:46:5)
  at async normalizedModule (node_modules/@nuxt/kit/dist/index.mjs:2140:17)
  at async installModule (node_modules/@nuxt/kit/dist/index.mjs:2397:95)
  at async initNuxt (node_modules/nuxt/dist/index.mjs:4669:5)
  at async loadNuxt (node_modules/nuxt/dist/index.mjs:4839:5)
  at async loadNuxt (node_modules/@nuxt/kit/dist/index.mjs:2627:19)
  at async Object.run (node_modules/nuxi/dist/chunks/prepare.mjs:61:18)
  at async runCommand$1 (node_modules/nuxi/dist/shared/nuxi.bd0a2fa0.mjs:1648:16)



 ERROR  Nuxt module should be a function: @nuxtjs/color-mode

error: postinstall script from "" exited with 1
bun add v1.1.34 (5e5e7c60)
[nuxt:tailwindcss] ℹ Using default Tailwind CSS file
```

## Steps to reproduce

- Create a new Nuxt project
- Install `shadcn-vue` with `bunx nuxi@latest module add shadcn-nuxt` or `npx nuxi@latest module add shadcn-nuxt`
- See how the error is thrown
