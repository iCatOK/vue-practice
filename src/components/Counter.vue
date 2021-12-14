<template lang="pug">
  .wrapper
    h1 Счётчик
    h2 {{counter}}
    button(@click="stopTimer") {{buttonText}}
</template>

<script>
export default {
  name: "Counter",
  data () {
    return {
      counter: 0,
      setIntervalInstance: null,
      isCounting: true,
      buttonText: "Остановить"
    }
  },
  mounted () {
    this.setIntervalInstance = setInterval(() => {
      this.counter++
    }, 1000)
  },
  methods: {
    stopTimer(){
      if(this.isCounting){
        clearInterval(this.setIntervalInstance);
        this.buttonText = "Запустить"
      } else {
        this.setIntervalInstance = setInterval(() => {
          this.counter++
        }, 1000)
        this.buttonText = "Остановить"
      }
      this.isCounting = !this.isCounting;
    }
  }
}
</script>

<style scoped>

</style>