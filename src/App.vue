<script setup lang="ts">
import { useStorage } from '@vueuse/core'
import {ref} from "vue"
import draggable from 'vuedraggable'
import {postDB} from "./db/post"

// 初始化数据
const state = useStorage('post', postDB, localStorage)
const drag = ref(false)

function log(value) {
  console.log(value)
}
</script>

<template>
  <draggable
      class="wrapper"
      :modelValue="state.data"
      @start="drag = true"
      @end="drag = false"
      item-key="index"
      @change="log"
  >
    <template #item="{ element }">
      <div class="item">
        <p>{{ element.name }}</p>
      </div>
    </template>
  </draggable>
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content: center;
  width: 100%;
}
.item {
  width: 100px;
  height: 100px;
  font-size: 20px;
  text-align: center;
  line-height: 100px;
  margin: 10px;
  background-color: #42b983;
  color: #ffffff;
}
</style>
