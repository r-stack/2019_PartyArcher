<template>
  <div class="container">
    <!--<div>テスト画面遷移</div>
    <ul>
      <li>
        <v-link href="/">Home</v-link>
        <v-link href="/about">About</v-link>
        <v-link href="/setting">Setting</v-link>
        <v-link href="/gacha">Gacha</v-link>
        <v-link href="/present">Present</v-link>
      </li>
    </ul>
    -->
    <slot></slot>
  </div>
</template>

<script>
  import VLink from '../components/VLink.vue'
  import axios from 'axios'

  export default {
    components: {
      VLink
    }
  }
</script>

<style scoped>
  html {
    height: 100%;
    width: 411px; 
    margin: 0px;
    padding: 0px 0px;
  }

  body {
    height: 100%;
    width: 411px; 
    margin: 0px;
    padding: 0px 0px;
  }
  .container {
    width: 411px; 
    height:731px;
    margin: 0px;
    padding: 0px 0px;
    background: #f9f7f5;
  }
</style>
