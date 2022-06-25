<template>
  <div>
    <h1>FIZZ BUZZ GUESSING GAME</h1>
    <form action="" @submit.prevent="fizzBuzzMethod">
      <input
        type="text"
        v-model="numberInput"
        placeholder="Test possible numbers..."
      />
      <input type="submit" />
    </form>
    <h2 v-if="fizz">Fizz</h2>
    <h2 v-else-if="buzz">Buzz</h2>
    <h2 v-else-if="fizzBuzz">FizzBuzz</h2>
    <h2 v-else>*crickets*</h2>
    <form action="" @submit.prevent="finalAnswer" id="answerForm">
      <p>Fizz:</p>
      <input
        type="text"
        v-model="fizzResponse"
        placeholder="Fizz Final Answer"
      />
      <p>Buzz:</p>
      <input
        type="text"
        v-model="buzzResponse"
        placeholder="Buzz Final Answer"
      />
      <p>FizzBuzz:</p>
      <input
        type="text"
        v-model="fizzBuzzResponse"
        placeholder="FizzBuzz Final Answer"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "FizzBuzz",
  data() {
    return {
      fizzValue: "",
      buzzValue: "",
      fizzBuzzValue: "",
      fizz: false,
      buzz: false,
      fizzBuzz: false,
      numberInput: "",
      fizzResponse: "",
      buzzResponse: "",
      fizzBuzzResponse: "",
    };
  },
  methods: {
    // Utility functions
    findGCD(n1, n2) {
      if (typeof n1 !== "number" || typeof y !== "number") return false;
      n1 = Math.abs(n1);
      n2 = Math.abs(n2);
      while (n2) {
        var t = n2;
        n2 = n1 % n2;
        n1 = t;
      }
      return n1;
    },
    findLCM(n1, n2) {
      let gcd = this.findGCD(n1, n2);
      return (n1 * n2) / gcd;
    },
    // In use functions
    setUp() {
      this.fizzValue = Math.floor(Math.random() * 10);
      let secondRandom = Math.floor(Math.random() * 10);
      if (secondRandom === this.fizzValue && secondRandom >= 5) {
        this.buzzValue = secondRandom - 1;
      } else if (secondRandom === this.fizzValue && secondRandom < 5) {
        this.buzzValue = secondRandom + 1;
      } else {
        this.buzzValue = secondRandom;
      }
      this.fizzBuzzValue = this.findLCM(this.fizzValue, this.buzzValue);
    },
    fizzBuzzMethod() {
      let i = parseInt(this.numberInput, 10);
      if (i % parseInt(this.fizzBuzzValue, 10) === 0) {
        this.fizzBuzz = true;
        this.fizz = false;
        this.buzz = false;
      } else if (i % parseInt(this.fizzValue, 10) === 0) {
        this.fizz = true;
        this.buzz = false;
        this.fizzBuzz = false;
      } else if (i % parseInt(this.buzzValue, 10) === 0) {
        this.buzz = true;
        this.fizz = false;
        this.fizzBuzz = false;
      } else {
        this.fizz = false;
        this.buzz = false;
        this.fizzBuzz = false;
      }
      if (i === parseInt(this.fizzBuzzValue, 10)) {
        alert("You got the Least Common Multiple. Please Input below");
      } else if (i === parseInt(this.fizzValue, 10)) {
        alert("You got the Base Fizz Value. Please Input below");
      } else if (i === parseInt(this.buzzValue, 10)) {
        alert("You got the Base Buzz Value. Please Input below");
      }
    },
  },
  mounted() {
    this.setUp();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#answerForm {
  display: flex;
  flex-direction: column;
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
