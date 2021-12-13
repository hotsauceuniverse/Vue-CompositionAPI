<template>
  <div @click="increase">{{ count }}</div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    let count = ref(0) // 일반 숫자로 하면 반응성이 없다. => ref / value 로 실행
    function increase() {
      count.value += 1
    } 

    return {
      count,
      increase
    }
  }
}
</script>
