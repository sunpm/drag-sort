<script setup lang="ts">
import { useStorage } from '@vueuse/core'
import {postDB} from "./db/post"

// 初始化数据
const state = useStorage('post', postDB, localStorage)

</script>

<template>

</template>

<style scoped>

</style>
