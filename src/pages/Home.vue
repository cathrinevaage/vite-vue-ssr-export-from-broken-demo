<template>
  <h1>Home</h1>
  <p>
    <img src="../assets/logo.png" alt="logo" />
  </p>
  <button @click="state.count++">count is: {{ state.count }}</button>
  <Foo />
  <p class="virtual">msg from virtual module: {{ foo.msg }}</p>
</template>

<script setup>
import foo from '@foo'
import { reactive, defineAsyncComponent } from 'vue'
import { test } from '../exportFromTest'
const Foo = defineAsyncComponent(() => import('../components/Foo').then(mod => mod.Foo))

console.log(`\x1b[34mTest is ${test !== undefined ? '\x1b[32m' : '\x1b[31m'}${test}\x1b[0m`)

const state = reactive({ count: 0 })
</script>

<style scoped>
h1,
a {
  color: green;
}
</style>
