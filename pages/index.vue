<template>
  <div class="container" :class="stuff.class">
    <div>
      <h1 class="title">{{stuff.text}}</h1>
      <img :src="stuff.giphy" alt>
      <h2 v-html="stuff.description" class="description"></h2>
    </div>
  </div>
</template>

<script>
const moment = require('moment');
export default {

  computed: {
    stuff: function() {
      moment.locale('nb')
      const currentDate = moment();
      const currentMonth = currentDate.month();
      const currentYear = currentDate.year();
      const nextYear = currentDate.year(currentYear + 1).year();

      const daysToPride = moment([nextYear, 5, 1]).toNow(true);

      if(currentMonth === 5)
      {
        return {text: "YAAAS", description: 'Happy <span class="p">p</span><span class="r">r</span><span class="i">i</span><span class="d">d</span><span class="e">e</span>', giphy: "https://media.giphy.com/media/3o7TKKFRj4mQDFZYhG/giphy.gif", class: "isPride", countdown: false}
      }
      else {
        return {text: "Nei...", description: `... Men det er bare <span> ${daysToPride} </span> igjen!`, giphy: "https://media.giphy.com/media/DnlUipYM3lMGc/giphy.gif", class: "notPride", countdown: true}
      }

      return today;
    }
  },
}
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-image: url("~assets/bakgrunn_ikkepride.jpg");
}

h1 {
  font-size: 50px;
  color: maroon;
  @media (min-width: 640px)
  {
    font-size: 100px;
  }
}

h2 {
  font-size: 25px;
  max-width: 420px;
  text-align: center;
  @media (min-width: 640px)
  {
    font-size: 50px;
  }
}

.isPride {
  background-image: url("~assets/Pridebakgrunn.jpg");

  h1,
  h2 {
    color: black;
    font-size: 50px;
    max-width: none;
    text-transform: uppercase;
    @media (min-width: 640px)
  {
    font-size: 100px;
  }

  }
  h2 {
    font-family: cursive;
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
  h2 span {
    display: block;
    color: maroon;
  }
}
</style>
