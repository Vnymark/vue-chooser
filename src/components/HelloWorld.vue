<template>
  <div class="container padding-sides">
    <table class="table is-striped is-fullwidth">
      <tbody>
        <tr v-for="(choice, index) in choices" :key="index">
          <td class="left"><p>{{ choice }}</p></td>
          <td class="right is-narrow">
            <button @click="removeChoice(index)" class="button is-danger is-medium">
              <span class="icon">
                <i class="fas fa-times"></i>
              </span>
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <div class="field has-addons">
      <div class="control is-expanded">
        <input v-model="inputChoice" class="input is-success is-medium" type="text">
      </div>
      <div class="control">
        <button @click="addChoice()" class="button is-success is-medium">Add</button>
      </div>
    </div>
    <div class="field control">
      <button @click="resetChoices()" class="button is-warning is-medium is-fullwidth">Remove all choices</button>
    </div>
    <div class="field control">
      <button @click="makeSelection()" class="button is-success is-medium is-fullwidth">Choose for me!</button>
    </div>
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
    resetChoices: function() {
      this.choices = [];
    },
    clearInput: function() {
      this.inputChoice = '';
    },
    makeSelection: function() {
      var amountOfChoices = this.choices.length;
      var selectedChoice = this.choices[Math.floor(Math.random() * amountOfChoices)];
      this.choices = [];
      this.choices.push(selectedChoice);
    },
    removeChoice: function(index) {
      this.choices.splice(index, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  margin-bottom: 10px;
}
li {
  position:relative;
  height:100%;
  p {
    font-size: 2.2em;
    margin: 0 10px;
    display:inline-block;
  }
  button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }
}
a {
  color: #42b983;
}

tbody {
  font-size: 2em;
}
.right {
  padding-right: 0;
  vertical-align: middle;
}
  .padding-sides {
    padding: 0 2em 0 2em;
  }
</style>
