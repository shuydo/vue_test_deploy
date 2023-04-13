If you need edit vite.config.js from:

"
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
})
"
to

"
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  base:'/[name repo on Git]/
  plugins: [vue()],
})
"

==================

DEPLOY:

yarn build

git add dist -f (after build) (-f for gitignore /dist)

git commit -m "comment"

git subtree push --prefix dist origin gh-pages
