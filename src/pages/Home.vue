<template>
  <main-layout>
    <div class="content">
      <div
        style="background-image: url(img/背景.png); background-repeat: no-repeat; background-size: cover; height:100%; width:100%;"
      >
        <p class="wallet">{{rs.wallet}}</p>
        <img src="img/chokin_frame.png" class="content1" width="220" height="50" alt />
        <img
          class="meter"
          src="img/chokin_meter.png"
          v-bind:style="{ width: computedWidth + 'px' }"
          height="50"
          alt
        />
        <img src="img/saihu.png" class="content2" width="191" height="100" alt />
        <v-link href="/gacha">
          <img src="img/gacha.png" width="150" height="150" alt class="content3" />
        </v-link>
      </div>
    </div>
  </main-layout>
</template>

<script>
import MainLayout from "../layouts/Main.vue";
import axios from "axios";
import VLink from "../components/VLink.vue";

export default {
  components: {
    MainLayout,
    VLink
  },
  data: function() {
    return {
      result: false,
      computedWidth: "30",
      isActive: false,
      hoges: "test11",
      rs: {
        wallet: "500",
        savings: "300",
        goal: "100"
      }
    };
  },
  methods: {
    start: function() {
      console.log("start");
      console.log(this.$data.rs);
      this.$data.computedWidth = Number(
        (Number(165) * Number(this.$data.rs.savings)) / this.$data.rs.goal
      );
      console.log(this.$data.computedWidth);
    }
  },
  mounted: function() {
    axios
      .get(
        "https://b820fpmdz4.execute-api.ap-northeast-1.amazonaws.com/dev/TeamArcher-GetStatus"
      )
      .then(
        function(response) {
          this.rs = response.data;
          this.start();
        }.bind(this)
      );
  }
};
</script>

<style scoped>
.content {
  position: relative;
  height: 100%;
  margin: 0px;
  width: 100%;
}
.content1 {
  position: absolute;
  left: 4px;
  top: 20px;
}
.wallet {
  font-size: 30px;
  z-index: 50;
  position: absolute;
  right: 40px;
  top: 26px;
}
.meter {
  z-index: 50;
  position: absolute;
  left: 5px;
  top: 20px;
  mater: 10px;
  object-fit: none;
  object-position: left;
}

.content2 {
  z-index: 20;
  position: absolute;
  top: 0px;
  left: 215px;
}

.content3 {
  position: absolute;
  top: 570px;
  left: 250px;
}
</style>
