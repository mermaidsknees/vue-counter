<template>
  <div class="mainCointainer">
    <div class="container" v-for="value of items" :key="value">
      <div class="counter">
         <button @click="increment(value)">+</button>
        <h1>{{value.counter}}</h1>
        <button @click="decrement(value)">-</button>  
      </div>
    </div>
    <div id="submit">
      <button type="submit" @click="submit(items)">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [{ counter: 0 }, { counter: 0 }, { counter: 0 }, { counter: 0 }]
      //asta cred ca putea sa fie mai easy fara object si nu ar fi nevoie de practici neortodoxe la submit
    };
  },
  methods: {
    increment(value) {
      value.counter >= 9 ? (value.counter = 0) : value.counter++;
    },
    decrement(value) {
      value.counter <= 0 ? (value.counter = 9) : value.counter--;
    },

    submit(items) {
      var correctCypher = "1234";
      var keys = [];
      items.forEach(item => keys.push(item.counter));
      var input = keys.join("");

      input === correctCypher
        ? console.log("Holy smokes, that's right!")
        : console.log("Mai incearca");
    }
  }
};
</script>

<style scoped>
body{
  /* align-items:center; */
}
.container {
  display: inline-flex;
  justify-content: center;
  padding:15px;
}
#submit {
  align-items: center;
}
</style>
