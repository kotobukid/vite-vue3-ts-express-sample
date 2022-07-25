<script setup lang="ts">
import {ref} from 'vue'
import _ from 'lodash'

defineProps<{ msg: string }>()

const count = ref(0)
const reset = () => {

    const highest: number = count.value
    const interval: number = 50
    _.map(_.range(count.value), (value: number, index: number) => {
            setTimeout(() => {
                count.value = value
            }, interval * (count.value - index))
        }
    )

    setTimeout(() => {
        count.value = 0
    }, interval * highest)
}
</script>

<template lang="pug">
h1 {{ msg }}

.card
    button(type="button" @click="count++") count is {{ count }}
    button(type="button" @click="reset") Reset
    p
        span Edit!!!&nbsp;
        code components/HelloWorld.vue
        span to test HMR

p
    span Check out
    a(href="https://vuejs.org/guide/quick-start.html#local" target="_blank") create-vue
    span , the official Vue + Vite starter

p
    span Install
    a(href="https://github.com/johnsoncodehk/volar" target="_blank") Volar
    span in your IDE for a better DX

p.read-the-docs Click on the Vite and Vue logos to learn more
</template>

<style scoped>
.read-the-docs {
    color: #888;
}
</style>
