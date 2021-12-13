<template>
  <h2 @click="increase">{{ count }}</h2>
  <h2 @click="changeMessage">{{ message }}</h2>
</template>

<script>
import { ref, computed, watch, onMounted } from 'vue'

export default {
  setup() { // component가 생성된 직후에 동작함 (onCreated라는 lifecycle은 존재하지 않아서, setup의 어디든 실행이 가능)
    const count = ref(0)
    const doubleCount = computed(() => {
      return count.value * 2
    })
    function increase() {
      count.value += 1
    }

    const message = ref('hello world')
    const reversedMessage = computed(() => {
      return message.value.split('').reverse().join('')
    })
    watch(message, newValue => {
      console.log(newValue)
    }) 
    function changeMessage() {
      message.value = 'Good'
    }
    console.log(message.value)

    onMounted(() => {
      console.log(count.value)
    })

    return {
      count,
      doubleCount,
      increase,
      message,
      changeMessage,
      reversedMessage
    }
  }
}
</script>