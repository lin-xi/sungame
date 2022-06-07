<template>
  <div class="home">
    <div class="project">
      <router-link to="/type"><div class="item">打字游戏</div></router-link>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
};
</script>

<style lang="less" scoped>
.project {
  .item {
    width: 140px;
    height: 140px;
    border-radius: 10px;
    background: rgb(37, 237, 80);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 26px;
    cursor: pointer;
    &:hover {
      background: rgb(3, 184, 24);
    }
  }
}
</style>
