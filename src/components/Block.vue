<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock:false,
      timer: null,
      reactionTime: 0

    };
  },
  methods: {
    startTimer(){
      this.timer = setInterval(() =>{
        this.reactionTime += 10
      },10)
      //this function is going to run every 10 milisecond

    },
    stopTimer(){
      clearInterval(this.timer)
      console.log(this.reactionTime)
      this.$emit('end', this.reactionTime)
    }
  },  
 
  mounted(){
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
      console.log(this.delay)
    },this.delay)
  }
}
    </script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
