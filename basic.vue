<template>
  <h2 @click="increase">{{ count }} / {{ doubleCount }}</h2>
  <h2 @click="changeMessage">{{ message }} / {{ reversedMessage }}</h2>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      message: 'hello world'
    }
  },

  computed: {
    doubleCount() {
      return this.count * 2
    },
    reversedMessage() {
      return this.message.split('').reverse().join('')
    }
  },

  watch: {
    message(newValue) {
      console.log(newValue)
    }
  },

  created() { // component가 생성된 직후에 실행이 되는 lifecycle
    console.log(this.message)
  },
  mounted() { // html과 component가 연결이 된 직후에 실행이 됨
    console.log(this.count)
  },

  methods: {
    increase() {
      this.count += 1
    },
    changeMessage() {
      this.message = 'Good'      
    }
  }
}
</script>