<template>
  <main>
   {{ boards.name }}
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
  mounted() {
  },
  methods: {
    
  },
};
</script>
<style lang="scss">
$VeryDarkBG: #20212C;
$DarkGrey: #2B2C37;
$LinesDark: #3E3F4E;
$MediumGrey: #828FA3;
$LinesLight: #E4EBFA;
$LightGreyLightBG: #F4F7FD;

$Black: #000112;
$White: #FFFFFF;
$Purple: #635FC7;
$PurpleHover: #A8A4FF;
$Red: #EA5555;
$RedHover: #FF9898;

$HeadingXL: 24px;
$HeadingL: 18px;
$HeadingM: 15px;
$HeadingS: 12px;


main {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: $VeryDarkBG;

}
</style>
