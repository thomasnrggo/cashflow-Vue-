<template>
  <Suspense>
    <template #default>
      <HomePage/>
    </template>
    <template #fallback>
      <SplashScreen/>
    </template>
  </Suspense>
</template>

<script>
import { defineAsyncComponent } from 'vue'
import SplashScreen from '@/components/SplashScreen.vue'

export default {
  name: 'App',
  components: {
    HomePage: defineAsyncComponent(() => 
      new Promise((resolve) => {
        setTimeout(() => {
          resolve(import('@/components/HomePage.vue'))
        }, 2000);
      })
    ),
    SplashScreen
}
}
</script>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
