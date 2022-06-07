<template>
  <div class="type-game">
    <div class="gamebox" ref="gameRef"></div>
  </div>
</template>

<script>
import * as PIXI from "pixi.js";
import { ref, reactive, onMounted } from "vue";
// @ is an alias to /src

export default {
  name: "TypeView",
  setup() {
    const gameRef = ref(null);
    const state = reactive({
      boxStyle: {},
    });

    let app;
    let container;
    const loader = new PIXI.Loader();

    onMounted(() => {
      app = new PIXI.Application({
        width: 1024,
        height: 512,
        resolution: window.devicePixelRatio || 1,
      });
      gameRef.value.appendChild(app.view);
      container = new PIXI.Container();
      app.stage.addChild(container);

      methods.gameStart();
    });

    const methods = {
      gameStart() {
        loader.baseUrl = "/typegame/images/";
        loader.add("zombie1", "zombies/zombie-1.png");
        loader.add(
          "zombie1-death",
          "/typegame/images/zombies/zombie-1-death.png"
        );
        loader.add("zombie2", "/typegame/images/zombies/zombie-2.png");
        loader.add(
          "zombie2-death",
          "/typegame/images/zombies/zombie-2-death.png"
        );
        loader.add("zombie3", "/typegame/images/zombies/zombie-3.png");
        loader.add(
          "zombie3-death",
          "/typegame/images/zombies/zombie-3-death.png"
        );
        loader.add("zombie4", "/typegame/images/zombies/zombie-4.png");
        loader.add(
          "zombie4-death",
          "/typegame/images/zombies/zombie-4-death.png"
        );
        loader.add("zombie5", "/typegame/images/zombies/zombie-5.png");
        loader.add(
          "zombie5-death",
          "/typegame/images/zombies/zombie-5-death.png"
        );
        loader.add("zombie6", "/typegame/images/zombies/zombie-6.png");
        loader.add(
          "zombie6-death",
          "/typegame/images/zombies/zombie-6-death.png"
        );
        loader.load(methods.resourceLoadFinish);
      },
      resourceLoadFinish() {
        var zombieSprite = new PIXI.Sprite(
          loader.resources["/typegame/images/zombies/zombie-1.png"].texture
        );
        //添加到舞台
        container.addChild(zombieSprite);
      },
    };

    return {
      gameRef,
      state,
    };
  },
};
</script>

<style lang="less" scoped>
.type-game {
  width: 100vw;
  height: 100vh;
  background: #222;
  display: flex;
  align-items: center;
  justify-content: center;
}
.gamebox {
  width: 1024px;
  height: 512px;
  background-repeat: no-repeat;
  background-image: url(../assets/typegame/images/background/bg-3.png);
  border: 10px #2a2a2a solid;
}
</style>
