<template>
  <div class="rounds__container">
    <div class="rounds__content">
      <div class="rounds__content--title">
        <span>Rodada 11 de 38</span>
      </div>
      <div class="rounds__content--matches">
        <div class="match-day-container">
          <!-- where the teams will stay -->
          <div class="match-day-teams">
            <div class="team">
              <div>
                <img src="https://apifutebol.s3.sa-east-1.amazonaws.com/escudos/5f999c95084cb.svg" alt="">
                <span>Flamengo</span>
              </div>
              <span>0</span>
            </div>
            <div class="team">
              <div>
                <img src="https://apifutebol.s3.sa-east-1.amazonaws.com/escudos/5f999e4424264.svg" alt="">
                <span>Cuiabá</span>
              </div>
              <span>0</span>
            </div>
          </div>
          <!-- where the info about status e date will stay -->
          <div class="match-day-info">
            <div>
              <span>FIM</span>
              <span>Ter, 07/06</span>
            </div>
          </div>
        </div>
        <div class="match-day-container">
          <!-- where the teams will stay -->
          <div class="match-day-teams">
            <div class="team">
              <span>Flamengo</span>
              <span>0</span>
            </div>
            <div class="team">
              <span>Cuiabá</span>
              <span>0</span>
            </div>
          </div>
          <!-- where the info about status e date will stay -->
          <div class="match-day-info">
            <div>
              <span>FIM</span>
              <span>Ter, 07/06</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
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
.rounds__container {
  width: ~"min(100vw, 800px)";
  margin: auto;

  .rounds__content--title {
    background: #171717;
    color: #bdc1c6;
    padding: 10px 20px;
  }

  .rounds__content--matches {
    display: grid;
    grid-template-columns: 1fr 1fr;
    color: #bdc1c6;
    background: #202124;
    border-top: 1px solid #3c4043;
    border-bottom: 1px solid #3c4043;

    .match-day-container {
      display: grid;
      grid-template-columns: 2fr 1fr;

      &:not(:last-child) {
        border-right: 1px solid #3c4043;
      }

      .match-day-teams {
        .team {
          margin: 30px 20px;
          display: flex;
          align-items: center;
          justify-content: space-between;

          div {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 10px;

            img {
              margin: 0;
              height: 24px;
            }
          }
        }
      }

      .match-day-info {
        display: flex;
        align-items: center;
        flex-direction: column;
        justify-content: center;
        padding: 30px 5px;

        & > div {
          border-left: 1px solid #3c4043;
          height: 100%;
          width: 100%;
          display: flex;
          flex-direction: column;
          align-items: center;
          justify-content: center;
        }
      }
    }
  }
}

</style>
