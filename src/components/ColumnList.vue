<script setup lang="ts"></script>
<script lang="ts">
import { defineComponent, PropType } from 'vue'
export interface ColumnProps {
  id: number
  title: string
  avatar?: string
  description: string
}
export default defineComponent({
  name: 'ColumnList',
  props: {
    list: {
      type: Array as PropType<ColumnProps[]>
    }
  },
  setup(props) {
    return props.list?.map(item => {
      if (!item.avatar) {
        item.avatar = require('.././assets/column.jpg')
      }
    })
  }
})
</script>
<template>
  <ul class="box">
    <li v-for="column in list" :key="column.id" class="card h-100 shadow-sm">
      <img :src="column.avatar" :alt="column.title" class="rounded-circle border border-light w-25 my-3" />
      <h5 class="card-title">{{ column.title }}</h5>
      <p class="card-text text-left">{{ column.description }}</p>
      <a href="#" class="btn btn-outline-primary">进入专栏</a>
    </li>
  </ul>
</template>
<style scoped>
.box {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-gap: 20px 20px;
  /* grid-template-rows: 1fr 1fr 1fr; */
}
li {
  display: grid;
  grid-template-rows: 1fr 1fr;
}
li img,
li a {
  justify-self: center;
}
li h5 {
  justify-self: center;
  align-self: end;
}
</style>
