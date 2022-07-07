<template>
  <div class="m-auto w-[350px] pt-[60px]">
    <div class="bg-slate-800 p-3 rounded grid grid-cols-4 gap-2 justify-items-center relative">
      <div class="absolute top-3.5 right-5">
      <span>{{ numberOne }}</span>
      <span>{{ sign }}</span>
      </div>
      <input
          class="mb-3 w-full rounded outline-slate-600 p-1 text-5xl text-center font-bold text-slate-800 bg-slate-300 col-span-4"
          v-model="inputData" readonly>
      <button :class="classButton" @click="clearAllItems()">AC</button>
      <button :class="classButton" @click="calculate('minus')">minus</button>
      <button :class="classButton" @click="calculate('%')">%</button>
      <button :class="classButton" @click="calculate('/')">/</button>
      <button :class="classButton" @click="onNumber('7')">7</button>
      <button :class="classButton" @click="onNumber('8')">8</button>
      <button :class="classButton" @click="onNumber('9')">9</button>
      <button :class="classButton" @click="calculate('*')">*</button>
      <button :class="classButton" @click="onNumber('4')">4</button>
      <button :class="classButton" @click="onNumber('5')">5</button>
      <button :class="classButton" @click="onNumber('6')">6</button>
      <button :class="classButton" @click="calculate('-')">-</button>
      <button :class="classButton" @click="onNumber('1')">1</button>
      <button :class="classButton" @click="onNumber('2')">2</button>
      <button :class="classButton" @click="onNumber('3')">3</button>
      <button :class="classButton" @click="calculate('+')">+</button>
      <button style="width: 156px" :class="[classButton, classLongButton]" @click="onNumber('0')">0</button>
      <button :class="classButton" @click="onNumber('.')">,</button>
      <button :class="classButton" @click="calculate('=')">=</button>
    </div>
    <h2>inputData:{{ inputData }}</h2>
    <h2>numberOne:{{ numberOne }}</h2>
    <h2>sign:{{ sign }}</h2>
  </div>
</template>

<script>
export default {
  name: "TheCalc",
  data() {
    return {
      inputData: "",
      numberOne: undefined,
      sign: undefined,
      classButton: ["text-xl", "font-bold", "text-slate-800", "rounded-full", "bg-slate-400", "hover:bg-slate-300", "w-[70px]", "h-[70px]"],
      classLongButton: ["col-span-2"]
    }
  },
  methods: {
    onNumber(n) {
      // if (this.inputData[0] !== n) {
      //   this.inputData = this.inputData + n;
      // } else {
      //   this.inputData = "0";
      // }
     this.inputData = this.inputData + n;
    },
    operation(a, opr, b) {
      a = Number(a);
      b = Number(b);
      let result;
      switch (opr) {
        case "+" :
          result = a + b;
          break;
        case "-" :
          result = a - b;
          break;
        case "*" :
          result = a * b;
          break;
        case "/" :
          result = a / b;
          break;
      }
      return result;
    },
    calculate(x) {
      this.inputData = Number(this.inputData )
      if(!this.numberOne) {
        this.numberOne = this.inputData;
        this.inputData = "";
      }
      if (x === "+") {
        if (this.sign) {
          this.numberOne = this.operation( this.numberOne, this.sign,this.inputData)
          this.inputData = "";
          this.sign = "";
        }
        this.sign = x;
      }
      if (x === "-") {
        if (this.sign) {
          this.numberOne = this.operation( this.numberOne, this.sign,this.inputData)
          this.inputData = "";
          this.sign = "";
        }
        this.sign = x;
      }
      if (x === "*") {
        if (this.sign) {
          this.numberOne = this.operation( this.numberOne, this.sign,this.inputData)
          this.inputData = "";
          this.sign = "";
        }
        this.sign = x;
      }
      if (x === "/") {
        if (this.sign) {
          this.numberOne = this.operation( this.numberOne, this.sign,this.inputData)
          this.inputData = "";
          this.sign = "";
        }
        this.sign = x;
      }
      if (x === "=") {
        this.inputData = this.operation( this.numberOne, this.sign,this.inputData)

          this.sign = "";
      }

    },
    clearAllItems() {
      this.inputData = "";
      this.numberOne = undefined;
      this.sign = undefined;
    }
  }
}
</script>

<style scoped>

</style>