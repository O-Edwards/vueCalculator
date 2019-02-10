<template>
  <div class="calculator">
    <input v-model="display" class="display" disabled>
    <button class="top-row" @click="clear">
      AC
    </button>
    <button class="top-row" @click="flip">
      +/-
    </button>
    <button class="top-row" @click="percentage">
      %
    </button>
    <button class="last-in-row" @click="divide">
      ÷
    </button>

    <button class="normal-row" @click="append('7')">
      7
    </button>
    <button class="normal-row" @click="append('8')">
      8
    </button>
    <button class="normal-row" @click="append('9')">
      9
    </button>
    <button class="last-in-row" @click="multiply">
      x
    </button>

    <button class="normal-row" @click="append('4')">
      4
    </button>
    <button class="normal-row" @click="append('5')">
      5
    </button>
    <button class="normal-row" @click="append('6')">
      6
    </button>
    <button class="last-in-row" @click="subtract">
      -
    </button>

    <button class="normal-row" @click="append('1')">
      1
    </button>
    <button class="normal-row" @click="append('2')">
      2
    </button>
    <button class="normal-row" @click="append('3')">
      3
    </button>
    <button class="last-in-row" @click="add">
      +
    </button>

    <button class="normal-row zero" @click="append('0')">
      0
    </button>
    <button class="normal-row" @click="dec">
      .
    </button>
    <button class="last-in-row" @click="equals">
      =
    </button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      display: '0',
      operatorClicked: false,
      operator: null,
      prev: null
    }
  },
  computed: {
    castedDisplay() {
      return Number(this.display)
    }
  },
  methods: {
    clear() {
      this.display = '0'
      this.operator = null
      this.prev = null
      this.operatorClicked = false
    },
    flip() {
      this.display = String(-1 * this.castedDisplay)
    },
    percentage() {
      this.display = String(this.castedDisplay / 100)
    },
    append(num) {
      if (this.display === '0') {
        this.display = num
      } else {
        this.display = `${this.display}${num}`
      }
    },
    dec() {
      this.display = this.display.indexOf('.') > -1 ? this.display : `${this.display}.`
    },
    multiply() {
      this.operator = (a, b) => a * b
      this.operations()
    },
    subtract() {
      this.operator = (a, b) => a - b
      this.operations()
    },
    add() {
      this.operator = (a, b) => a + b
      this.operations()
    },
    divide() {
      this.operator = (a, b) => a / b
      this.operations()
    },
    operations() {
      this.prev = this.display
      this.operatorClicked = true
      this.display = '0'
    },
    equals() {
      this.display = this.operator(this.prev, Number(this.display))
      this.operatorClicked = false
    }
  }
}
</script>
>
<style>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  background-color: black;
}

.display {
  grid-column: 1/5;
  font-size: 3rem;
  background-color: black;
  color: white;
  font-size: 3rem;
  margin-bottom: .5rem;
  outline: none;
  border: none;
  text-align: right;
  padding-right: 4rem;
}

button {
  border-radius: 50%;
  height: 4rem;
  width: 4rem;
  outline: none;
  font-size: 1.75rem;
  text-align: center;
  outline: none;
  border: none;
  cursor: pointer;
  margin-bottom: .50rem;
}

.top-row {
  background-color: #95a5a6;
  color:black;
}
.normal-row{
  background: #1e272e;
  color: white;
}
.last-in-row {
  background-color:#e67e22;
  color: white;
}
.zero {
  grid-column: 1/3;
  /* width: 85%;
  border-radius: 40%; */
}

</style>
