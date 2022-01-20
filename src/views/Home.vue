<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <MapPane></MapPane>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue';
// マップコンポーネント読み込み
import MapPane from '@/components/MapPane.vue';

@Options({
  components: {
    HelloWorld,
    MapPane
  },
})
export default class Home extends Vue {}
</script>
