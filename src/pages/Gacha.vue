<template>
  <main-layout>
    <div class="content">
      <div class="gachagachas" v-show="!result" v-bind:class="{ smile: isActive }" v-on:animationend="next(item)"></div>
      <div class="gacha_result_present" v-show="result_present"  >
      </div>
      <div class="gacha_result" v-show="result_result"  >
        <p class="b_text"> おめでとう<br>{{ gacha.gain }} P<br>を手に入れた</p>
      </div>
    </div>
  </main-layout>
</template>

<script>
  import MainLayout from '../layouts/Main.vue'
  import axios from 'axios'

  export default {
    components: {
      MainLayout
    },
    data: function() {
      return {
        result: false,
        result_result: false,
        result_present: false,
        isActive: false,
        hoges: "test11",
        gacha: "test111"
      }
    },
    methods: {
      start: function () {
        this.$data.isActive = !this.$data.isActive
      },
      next: function(){
        this.$data.result = !this.$data.result;
        this.$data.result_result = !this.$data.result_result;
        console.log(this.$data.gacha)
        if(this.$data.gacha.reward){
          setTimeout(() => {
            this.$data.result=true;
            this.$data.result_result=false;
            this.$data.result_present  = true; 
          }, 3000);
        }
      }
    },
    mounted: function () {
      axios
      .get('https://b820fpmdz4.execute-api.ap-northeast-1.amazonaws.com/dev/TeamArcher-Gacha')
      .then(response => (this.gacha = response.data));
      this.start();
    }
  }
</script>

<style scoped>
  .content {
      height: 100%;
      margin: 0px;
      width: 100%; 
  }
  .gacha_result{
    position:relative; 
    background-image: url("/img/リザルト.png");
    background-size: 100%;
    width: 100%; 
    height: 100%;
  }
  .gacha_result_present{
    position:relative; 
    background-image: url("/img/荷物.png");
    background-size: 100%;
    width: 100%; 
    height: 100%;
  }
  .gachagachas {
    position:relative; 
    background-image: url("/img/gatya.png");
    background-size: cover;
    height: 100%;
  }
  .b_text {
    font-size: 60px;
    color: white;
    z-index: 50;
  		position: absolute;  
      left: 60px;
        top: 200px;dd
  }
  .smile {
    animation: animationSmile 2s steps(30) 1;
  }
  @keyframes animationSmile {
    to {
      background-position: -12330px 0;
    }
  }
</style>
