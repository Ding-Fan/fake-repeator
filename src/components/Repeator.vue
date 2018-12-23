<template>
  <div>
    <div>
      <div>
        <div v-for="(message, index) in messages" :key="index">
          {{ message }}
        </div>
      </div>
    </div>
    <div>

    <input
      type="text"
      v-model="mainInput"
      @keyup.enter="submit"
    >
    </div>
    <div>

    </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      mainInput: '',
      messages: [],
    }
  },
  methods: {
    submit() {
      this.messages.push(this.mainInput)
      this.messages.push(this.reply(this.mainInput))
      this.mainInput = ''
    },
    reply(sentence) {
      let result = sentence
      if ((/吗？?/).test(sentence)) {
        result = result.replace(/吗？?/, '!')
      }
      if((/我/).test(sentence)) {
        result = result.replace(/我/, '你')
      }
      if((/范鼎/).test(sentence)) {
        result = result.replace(/范鼎/, '高楚钢')
      }
      

      return result
    }
  },
}
</script>

<style scoped>
</style>