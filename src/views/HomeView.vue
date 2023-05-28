<template>
  <main>
    <div class="categories">
      <div class="todo categorie">
        <div class="circle"></div>
        <h3 class="header">TODO</h3>
      </div>
      <div class="doing categorie">
        <div class="circle"></div>
        <h3 class="header">DOING</h3>
      </div>
      <div class="done categorie">
        <div class="circle"></div>
        <h3 class="header">DONE</h3>
      </div>
    </div>
  </main>
</template>
<script>
import dataJSON from "/data/data.json";

export default {
  data() {
    return {
      boards: dataJSON,
    };
  },
  mounted() {},
  methods: {},
};
</script>
<style lang="scss">
$VeryDarkBG: #20212c;
$DarkGrey: #2b2c37;
$LinesDark: #3e3f4e;
$MediumGrey: #828fa3;
$LinesLight: #e4ebfa;
$LightGreyLightBG: #f4f7fd;

$Black: #000112;
$White: #ffffff;
$Purple: #635fc7;
$PurpleHover: #a8a4ff;
$Red: #ea5555;
$RedHover: #ff9898;

$HeadingXL: 24px;
$HeadingL: 18px;
$HeadingM: 15px;
$HeadingS: 12px;

main {
  padding-top: 120px;
  padding-left: 2rem;
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: row;
  background: $VeryDarkBG;
  .categories {
    width: 100%;
    height: fit-content;
    display: flex;
    .categorie {
      width: 280px;
    }
    .todo {
      display: flex;
      align-items: center;
      column-gap: 0.6rem;

      .circle {
        background: #49c4e5;
      }
    }
    .doing {
      display: flex;
      align-items: center;
      column-gap: 0.6rem;

      .circle {
        background: #8471f2;
      }
    }
    .done {
      display: flex;
      align-items: center;
      column-gap: 0.6rem;

      .circle {
        background: #67e2ae;
      }
    }
  }
}
.header {
  font-size: $HeadingS;
  color: $MediumGrey;
  letter-spacing: 2.4px;
  font-weight: bold;
}
.circle {
  width: 15px;
  height: 15px;
  border-radius: 50%;
}
</style>
