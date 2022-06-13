<template>
  <div id="app__container">
    <div class="nav">
      <div class="nav__title">
        <span>Brasileirão - Série A</span>
      </div>
      <div class="nav__options">
        <router-link to="/">Partidas</router-link>
        <router-link to="/placing">Classificação</router-link>
      </div>
    </div>
    <div class="views">
      <router-view/>
    </div>
  </div>
</template>

<style lang="less">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}

#app__container {
  min-height: 100vh;
  background-color: #303134;
}

.nav {
  background-color: #10502f;
  color: #fff;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 10px 0 rgba(0, 0, 0);

  &__title {
    padding: 10px 20px;

    font-size: 16px;
    line-height: 20px;
    font-weight: bold;
  }

  &__options {
    display: flex;
    align-items: flex-end;
    justify-content: center;
    gap: 20px;

    height: 100px;

    a {
      text-transform: uppercase;
      text-decoration: none;
      color: #fff;

      padding: 15px 20px;

      font-size: 12px;
      font-weight: bold;

      opacity: 0.7;

      &:hover {
        opacity: 1;
        background: rgba(43, 168, 91, 0.2);
      }

      &.router-link-exact-active {
        opacity: 1;
        border-bottom: 3px solid #fff;
        background: rgba(43, 168, 91, 0.2);
      }
    }
  }
}
</style>
