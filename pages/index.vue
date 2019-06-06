<template>
  <div class="container" :class="stuff.class">
    <div>
      <h1 class="title">{{stuff.text}}</h1>
      <img :src="stuff.giphy" alt="">
      <h2 v-html="stuff.description" class="description"></h2>
    </div>
  </div>
</template>

<script>
const moment = require('moment');
export default {

  computed: {
    stuff: function() {
      const currentDate = moment();
      const currentMonth = currentDate.month();
      const currentYear = currentDate.year();
      const nextYear = currentDate.year(currentYear + 1).year();

      console.log(currentMonth);
      console.log(currentYear);
      console.log(nextYear);
      // const nextJune = moment();
      // console.log("next", nextJune);

      if(currentMonth === 5)
      {
        return {text: "YAAAS", description: "Happy <span> pride </span>", giphy: "https://media.giphy.com/media/3o7TKKFRj4mQDFZYhG/giphy.gif", class: "isPride", countdown: false}
      }
      else {
        return {text: "Nei", description: `... Men det er bare <span> ${nextYear} </span> dager igjen!`, giphy: "https://media.giphy.com/media/DnlUipYM3lMGc/giphy.gif", class: "", countdown: true}
      }

      return today;
    }
  },
}
</script>

<style lang="scss" scoped>
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

  &.isPride {
    background-image: url("~assets/Pridebakgrunn.jpg");

    .description, .title {
      font-size: 100px;

      span {
        color: rebeccapurple;
        text-transform: uppercase;
      }
    }
  }
}
</style>
