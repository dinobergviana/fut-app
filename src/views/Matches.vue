<template>
  <div class="matches"></div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
// import axios from 'axios';

@Component({
  components: {},
})
export default class Home extends Vue {
  // private apiKey = 'live_38e06ca1acea3770a689a24d7eac77'
  // private async getPlacing() {
  //   const response = await axios.get('https://api.api-futebol.com.br/v1/campeonatos/10/rodadas/11', {
  //     headers: {
  //       Authorization: `Bearer ${this.apiKey}`,
  //     },
  //   });
  //   console.log(response);
  // }
}
</script>

<style lang="less" scoped>
.matches {
  width: ~"min(100vw, 800px)";
  margin: auto;
}
</style>
