<template>
  <div class="placing">
    <div class="placing__container">
      <table>
        <thead>
          <tr>
            <th class="th__club">Clube</th>
            <th>Pts</th>
            <th>PJ</th>
            <th>Vit</th>
            <th>E</th>
            <th>DER</th>
            <th>GP</th>
            <th>GC</th>
            <th>SG</th>
            <th class="club__last-five">Últimas cinco</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="team in tableTeams" :key="team.posicao">
            <td class="club">
              <div>
                <span>{{ team.posicao }}</span>
              </div>
              <span class="club-image">
                <img :src="team.time.escudo" alt="">
              </span>
              <span>{{ team.time.nome_popular }}</span>
            </td>
            <td style="text-align: center;">{{ team.pontos }}</td>
            <td>{{ team.jogos }}</td>
            <td>{{ team.vitorias }}</td>
            <td>{{ team.empates }}</td>
            <td>{{ team.derrotas }}</td>
            <td>{{ team.gols_pro }}</td>
            <td>{{ team.gols_contra }}</td>
            <td>{{ team.saldo_gols }}</td>
            <td class="td__last-five">
              <img
                v-for="(item, index) in team.ultimos_jogos"
                :key="team.posicao + index" src="../assets/images/check-circle.svg"
                alt=""
              />
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import placingTable from '@/assets/mocks/table';
import { ITeam } from './Matches.vue';

interface ITableTeam {
  posicao: number;
  pontos: number;
  time: ITeam;
  jogos: number;
  vitorias: number;
  empates: number;
  derrotas: number;
  gols_pro: number;
  gols_contra: number;
  saldo_gols: number;
  ultimos_jogos: string[];
}

@Component
export default class Placing extends Vue {
  public tableTeams: ITableTeam[] = []

  private created() {
    this.tableTeams = placingTable.table['taca-guanabara-fase-de-grupos']['grupo-principal'];
  }
}
</script>

<style lang="less" scoped>
.placing {
  width: ~"min(100vw, 800px)";
  margin: 0 auto;
  overflow-x: auto;
}

.placing__container {
  display: block;
  width: 100%;
  overflow-x: auto;
  border-right: 1px solid #3c4043;
  border-left: 1px solid #3c4043;

  table {
    width: 100%;
    border-spacing: 0 0;
    color: #bdc1c6;

    thead tr {
      background-color: #171717;

      .th__club {
        min-width: 260px;
        text-align: left;
      }

      th {
        padding: 15px 10px;
      }
    }

    tbody tr {
      td {
        border-bottom: 1px solid #3c4043;
        padding: 10px 15px;
        background: #202124;

        .club-image {
          display: flex;
          align-items: center;
          img {
            height: 24px;
          }
        }

        &:not(:first-child) {
          text-align: center;
        }
      }

      .club {
        display: flex;
        align-items: center;
        gap: 15px;

        div {
          padding: 5px;
          height: 24px;
          width: 24px;
          display: flex;
          align-items: center;
          justify-content: center;
        }
      }

      .td__last-five {
        min-width: 140px;
      }
    }
  }
}
</style>
