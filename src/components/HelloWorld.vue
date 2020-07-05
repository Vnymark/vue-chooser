<template>
  <div class="input">
    <ul>
      <li v-for="choice in choices" :key="choice">
      {{ choice }}
      </li>
    </ul>
  <input v-model="inputChoice" type="text"/>
  <button @click="addChoice()">Add choice</button>
    <button @click="makeSelection()">Choose for me!</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data: function () {
    return {
      choices: [],
      inputChoice: ''
    }
  },
  props: {
    msg: String
  },
  methods: {
    addChoice() {
      this.choices.push(this.inputChoice);
      this.clearInput();
    },
    clearInput: function() {
      this.inputChoice = '';
    },
    makeSelection: function() {
      var amountOfChoices = this.choices.length;
      var selectedChoice = this.choices[Math.floor(Math.random() * amountOfChoices)];
      this.choices = [];
      this.choices.push(selectedChoice);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
/*ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}*/
a {
  color: #42b983;
}
</style>
