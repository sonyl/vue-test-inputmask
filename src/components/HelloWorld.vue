<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="value" v-mask="options" maxlength="42">
    <div>{{ value }}</div>
  </div>
</template  >

<script>
import Inputmask from 'inputmask';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  directives: {
    mask: {
      bind: function(el, binding) {
        Inputmask(binding.value).mask(el);
      }
    }
  },
  data() {
    return {
      value: 'DE12123456780123456789',
      options: {
        mask: 'AA** **** **** **** **** **[** **** **** **]',
        greedy: false,
        casing: 'upper',
        definitions: {
            "*": {
              validator: "[0-9A-Za-z]"
            }
        },
        placeholder: "_",
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  font-size: 2em;
  width: 30em;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>