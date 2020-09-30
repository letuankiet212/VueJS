<template>
  <div class="calculator">
   
    <div class="result">
      <div class="demo">{{demo}}</div>
      {{ show }}
    </div>
    <div v-on:click="clear()">AC</div>
    <div v-on:click="dau()">+/-</div>
    <div>%</div>
    <div
      v-on:click="cong('chia')"
      style="background-color: #f69733; color: white"
    >
      /
    </div>
    <div v-on:click="number(7)">7</div>
    <div v-on:click="number(8)">8</div>
    <div v-on:click="number(9)">9</div>
    <div
      v-on:click="cong('nhan')"
      style="background-color: #f69733; color: white"
    >
      X
    </div>
    <div v-on:click="number(4)">4</div>
    <div v-on:click="number(5)">5</div>
    <div v-on:click="number(6)">6</div>
    <div
      v-on:click="cong('tru')"
      style="background-color: #f69733; color: white"
    >
      -
    </div>
    <div v-on:click="number(1)">1</div>
    <div v-on:click="number(2)">2</div>
    <div v-on:click="number(3)">3</div>
    <div
      v-on:click="cong('cong')"
      style="background-color: #f69733; color: white"
    >
      +
    </div>
    <div v-on:click="number(0)" class="zero">0</div>
    <div>.</div>
    <div v-on:click="kq()" style="background-color: #f69733; color: white">
      =
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  props: {
    msg: String,
  },
  data() {
    return {
      result: 0,
      numberA: 0,
      numberB: 0,
      show: "",
      dau: "",
      demo :"",
    };
  },
  methods: {
    number($data) {
      if (this.show.length >= 6) {
        alert("Đã đạt tới giới hạn");
      }
       else if (this.result != 0) {
        alert("Vui lòng chọn lại số ");
        this.show = "";
        this.result = 0;
        this.demo = ""
      } 
      else {
        this.show = this.show + $data;
        this.demo = this.demo + this.show ;
      }
    },
    clear() {
      this.show = "";
      this.result = 0;
      this.numberA = 0;
      this.numberB = 0;
      this.dau = "";
      this.demo = ""
    },
    cong($dau) {
      // if (this.numberA = 0) {
      //   alert("Vui lòng nhập số trước khi nhập dấu");
      //   console.log($dau)
      // }
      // } else {
      this.numberA = parseInt(this.show);
      this.show = "";
      this.dau = $dau;
      this.demo = this.demo + $dau
      // }
    },
    kq() {
      this.numberB = parseInt(this.show);
      if (this.dau === "cong") {
        this.result = this.numberA + this.numberB;
      } else if (this.dau === "tru") {
        this.result = this.numberA - this.numberB;
      } else if (this.dau === "nhan") {
        this.result = this.numberA * this.numberB;
      } else if (this.dau === "chia") {
        this.result = this.numberA / this.numberB;
      }

      this.show = this.result;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(39px, auto);
  width: 200px;
  margin: 0 auto;
  align-items: center;
  font-size: 13px;
}
.calculator .result .demo {
  height: 10px;
  line-height: 1;
  font-size: 10px;
}
.calculator > div {
  cursor: pointer;
  height: 100%;
  line-height: 39px;
  font-weight: 600;
  background-color: #e6e6e6;
  outline: 1px solid #aaaaaa;
}
.calculator > div:hover {
  transition: 0.5s all;
  box-shadow: 1px 1px 5px black;
  z-index: 2;
}
.calculator .result {
  grid-column: 1/5;
  background-color: #30518d !important;
  height: 58px;
  text-align: right;
  font-size: 50px;
  align-items: end;
  color: white;
  line-height: 1;
}
.calculator .zero {
  grid-column: 1/3;
}
</style>
