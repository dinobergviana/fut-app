<template>
  <div class="rounds__container">
    <div class="rounds__content">
      <div class="rounds__content--title">
        <span>Rodada {{ matchNumber }} de 38</span>
      </div>
      <div class="rounds__content--matches">
        <div v-for="(match, index) in matchesOfTheDay" class="match-day-container" :key="index">
          <!-- where the teams will stay -->
          <div class="match-day-teams">
            <div class="team">
              <div>
                <img :src="match.time_mandante.escudo" alt="">
                <span>{{ match.time_mandante.nome_popular }}</span>
              </div>
              <span>{{ match.placar_mandante }}</span>
            </div>
            <div class="team">
              <div>
                <img :src="match.time_visitante.escudo" alt="">
                <span>{{ match.time_visitante.nome_popular }}</span>
              </div>
              <span>{{ match.placar_visitante }}</span>
            </div>
          </div>
          <!-- where the info about status e date will stay -->
          <div class="match-day-info">
            <div>
              <span>{{ match.status | matchStatus }}</span>
              <span>{{ match.data_realizacao | matchDate }}</span>
              <span>{{ match.hora_realizacao }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import matchesMock from '@/assets/mocks/matches';
// import axios from 'axios';

export interface ITeam {
  nome_popular: string;
  escudo: string;
}

interface IMatchData {
  time_mandante: ITeam;
  time_visitante: ITeam;
  placar_mandante: number | null;
  placar_visitante: number | null;
  status: string;
  data_realizacao: string;
}

@Component({
  filters: {
    matchStatus(status: string): string {
      if (status === 'finalizado') {
        return 'FIM';
      }
      return status[0].toUpperCase() + status.slice(1, status.length);
    },
    matchDate(date: string): string {
      return date;
    },
  },
})
export default class Home extends Vue {
  public matchesOfTheDay!: IMatchData[];
  public matchNumber = 0;

  // private apiKey = 'live_38e06ca1acea3770a689a24d7eac77'
  // private async getPlacing() {
  //   const response = await axios.get('https://api.api-futebol.com.br/v1/campeonatos/10/rodadas/11', {
  //     headers: {
  //       Authorization: `Bearer ${this.apiKey}`,
  //     },
  //   });
  //   console.log(response);
  // }

  private setMatches(): void {
    this.matchNumber = matchesMock.matches.rodada;
    this.matchesOfTheDay = matchesMock.matches.partidas;
  }

  private created(): void {
    this.setMatches();
  }
}
</script>

<style lang="less" scoped>
.rounds__container {
  width: ~"min(100vw, 800px)";
  margin: auto;

  .rounds__content--title {
    background: #171717;
    color: #bdc1c6;
    padding: 15px 10px;
  }

  .rounds__content--matches {
    display: grid;
    grid-template-columns: 1fr 1fr;
    color: #bdc1c6;
    background: #202124;
    border-top: 1px solid #3c4043;

    .match-day-container {
      display: grid;
      grid-template-columns: 2fr 1fr;
      border-bottom: 1px solid #3c4043;

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
          font-size: 14px;
        }
      }
    }
  }
}

</style>
