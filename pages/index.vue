<template>
  <div class="container" :class="stuff.class">
    <div class="hideForDesktop iconsRow">
      <img src="~/assets/jenter.png" alt>
      <img src="~/assets/gutter.jpg" alt>
      <img src="~/assets/trans.png" alt>
    </div>

    <img src="~/assets/gayflagg.png" alt class="hideForDesktop gayflag flag">
    <img src="~/assets/transflagg.png" alt class="hideForDesktop transflag flag">
    <img src="~/assets/babaSHOOK.png" alt class="hideForDesktop babadook">
    <img src="~/assets/daldo.png" alt class="hideForDesktop dildo">
    <img src="~/assets/tristfjes.png" alt class="hideForPride trist">
    <img src="~/assets/tristfjes.png" alt class="hideForPride trist trist2">
    <img src="~/assets/tristfjes.png" alt class="hideForPride trist trist3">
    <div class="content">
      <h1 class="title">{{stuff.text}}</h1>
      <img :src="stuff.giphy" alt="">
      <h2 v-html="stuff.description" class="description"></h2>
    </div>
  </div>
</template>

<script>
const moment = require("moment");
export default {
  computed: {
    stuff: function() {
      moment.locale("nb");
      const currentDate = moment();
      const currentMonth = currentDate.month();
      const currentYear = currentDate.year();
      const nextYear = currentDate.year(currentYear + 1).year();

      const daysToPride = moment([nextYear, 5, 1]).toNow(true);

      if (currentMonth === 5) {
        return {
          text: "YAAAS",
          description:
            'Happy <span class="p">p</span><span class="r">r</span><span class="i">i</span><span class="d">d</span><span class="e">e</span>',
          giphy: "https://media.giphy.com/media/3o7TKKFRj4mQDFZYhG/giphy.gif",
          class: "isPride",
          countdown: false
        };
      } else {
        return {
          text: "Nei...",
          description: `... Men det er bare <span> ${daysToPride} </span> igjen!`,
          giphy: "https://media.giphy.com/media/DnlUipYM3lMGc/giphy.gif",
          class: "notPride",
          countdown: true
        };
      }

      return today;
    }
  }
};
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  padding: 0 2rem;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-image: url("~assets/bakgrunn_ikkepride.jpg");
  overflow: hidden;
}
h1 {
  font-size: 50px;
  color: maroon;
  @media (min-width: 640px) {
    font-size: 100px;
  }
}

h2 {
  font-size: 25px;
  max-width: 420px;
  text-align: center;
  @media (min-width: 640px) {
    font-size: 50px;
  }
}

.content {
  z-index: 2;
}

.isPride {
  background-image: none;
  @media (min-width: 960px) {
    background-image: url("~assets/Pridebakgrunn.jpg");
  }
  .hideForPride {
    display: none;
  }

  .hideForDesktop {
    @media (min-width: 960px) {
      display: none;
    }
  }

  .iconsRow {
    display: flex;
    justify-content: space-around;
    align-items: center;
    position: absolute;
    top: 20px;
    left: 0;
    width: 100%;
    height: 30px;
    @media (min-width: 960px) {
      display: none;
    }

    img {
      height: 30px;
      width: auto;
    }
  }

  .flag {
    position: absolute;
    top: 50%;
    z-index: -1;
    &.gayflag {
      left: -20px;
      transform: translate3d(-50%, -100%, 0);
    }
    &.transflag {
      right: -9px;
      transform: translate3d(50%, -100%, 0);
    }
  }

  .babadook {
    position: absolute;
    top: 100%;
    left: -140px;
    transform: translate3d(0, -100%, 0);
    z-index: -1;
    height: 300px;
  }
  .dildo {
    position: absolute;
    top: 100%;
    right: -140px;
    transform: translate3d(0, -100%, 0) rotate(-8deg);
    z-index: -1;
    height: 300px;
  }

  h1,
  h2 {
    color: black;
    font-size: 50px;
    max-width: none;
    text-transform: uppercase;
    @media (min-width: 640px) {
      font-size: 100px;
    }
  }
  h2 {
    font-family: "comic sans";
  }
}

.p {
  color: red;
}
.r {
  color: yellow;
}
.i {
  color: green;
}
.d {
  color: blue;
}
.e {
  color: blueviolet;
}

.notPride {
  .hideForPride {
    @media (min-width: 960px) {
      display: none;
    }
  }
  .hideForDesktop {
    display: none;
  }
  h2 span {
    display: block;
    color: maroon;
  }

  .trist {
    position: absolute;
    top: 10%;
    left: 10%;
    transform: translate3d(-50%, -50%, 0);
    width: 100px;
    height: auto;

    &.trist2 {
      top: 28%;
      left: 84%;
    }
    &.trist3 {
      top: 90%;
      left: 70%;
    }
  }
}
</style>
