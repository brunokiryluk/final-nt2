<template>
  <section class="text-validator">
    <div>
      <h1>Final nt2</h1>
      <input
        type="text"
        placeholder="Ingrese cualquier texto"
        v-model="inputText"
        @input="incrementar()"
      />
      <!--@input= "showText" @input="replaceLetters()-->

      <h2 v-if="inputText.length > 0"> Cantidad: {{ this.getInputTextLength }}</h2>
      <h2 v-if="inputText.length > 0">{{ this.replaceLetters() }} (Codificado)</h2>
      <h2 v-if="inputText.length > 0">{{ this.inputText.toUpperCase() }} (Mayuscula)</h2>
      <h2 v-if="inputText.length > 0">{{ getInputTextToLowerCase }} (Minuscula)</h2>
      <h2 v-if="inputText.length > 0"> {{this.upperLower()}}(Mayuscula/minuscula)</h2>
      <h2 v-if="inputText.length > 0"> {{this.lowerUpper()}} (Minuscula/mayuscula)</h2>

      <p><p>respuestas: 1:A 2:B 3:C,D(porque un trim recorta los espacios en toda una cadena de texto. Ya sea adelante, atras o en el medio) 4:B 5: B,C  </p>
    </div>
  </section>
</template>

<script>
export default {
  name: "text-validator",
  props: [],
  mounted() {},
  data() {
    return {
      inputText: "",
      contador: -1
      //isUpper: true,
    };
  },
  methods: {
    showText() {
      console.log(this.getInputTextToLowerCase);
    },
    incrementar() {
        this.contador++
        console.log(this.contador);
      },
    replaceLetters() {
      let input = this.getInputTextToLowerCase;
      let inputAsArray = input.split('').map(function(element) { 
        element = element.replace('a', 'u');
        element = element.replace("e", "o");
        element = element.replace("o", "e");
        element = element.replace("u", "a");
        return element;
      })
      console.log(inputAsArray);
      input = inputAsArray.join("")
       return input;
      //return inputAsArray;
    },
    upperLower() {
      let input = this.getInputTextToLowerCase.split("");
      let isUpper = true;
      let inputAsArray = input.map(function(element) {
       if (isUpper) {
         element = element.toUpperCase()
       } else {
         element = element.toLowerCase()
       }
        isUpper = !isUpper;
        return element;
      });
      console.log(inputAsArray);
      input = inputAsArray.join("")
      return input;
    },
    lowerUpper() {
      let input = this.getInputTextToLowerCase.split("");
      let isUpper = false;
      let inputAsArray = input.map(function(element) {
       if (isUpper) {
         element = element.toUpperCase()
       } else {
         element = element.toLowerCase()
       }
        isUpper = !isUpper;
        return element;
      });
      console.log(inputAsArray);
      input = inputAsArray.join("")
      return input;
    },
  },
  computed: {
    getInputTextToLowerCase() {
      console.log(this.inputText.toLowerCase());
      return this.inputText.toLowerCase();
    },
    getInputTextLength() {
      return this.inputText.length;
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
