<template>
  <div class="keyboard">
    <!-- 1 -->
    <div class="btn-style" @click="trackKey(7)">7</div>
    <div class="btn-style" @click="trackKey(8)">8</div>
    <div class="btn-style" @click="trackKey(9)">9</div>
    <div class="btn-style" @click="trackKey('/')">/</div>
    <!-- 2 -->
    <div class="btn-style" @click="trackKey(4)">4</div>
    <div class="btn-style" @click="trackKey(5)">5</div>
    <div class="btn-style" @click="trackKey(6)">6</div>
    <div class="btn-style" @click="trackKey('*')">*</div>
    <!-- 3 -->
    <div class="btn-style" @click="trackKey(1)">1</div>
    <div class="btn-style" @click="trackKey(2)">2</div>
    <div class="btn-style" @click="trackKey(3)">3</div>
    <div class="btn-style" @click="trackKey('-')">-</div>
    <!-- 4 -->
    <div class="btn-style" @click="trackKey('0')">0</div>
    <div class="btn-style" @click="trackKey('.')">.</div>
    <div class="btn-style" @click="trackKey('+')">+</div>
    <div class="btn-style equal" @click="equal">=</div>

    <div class="btn-style reset" @click="reset">
      <i class="fas fa-trash-alt"></i>
    </div>
    <div class="btn-style del" @click="remove">
        <i class="fas fa-redo"></i>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      sy: "",
    };
  },
  methods: {
    trackKey(param) {
      let data = {
        stroke: "",
        value: param,
      };

      this.sy += param;
      this.$emit("displayTrack", data);
    },
    reset() {
      let data = {
        stroke: "reset",
        value: '',
      };
      this.$emit("displayTrack", data);
      this.sy = "";
    },
    equal() {
      var finalValue = eval(this.sy);
      if(finalValue < 1)
      {
         finalValue = eval(this.sy).toFixed(2);
      }
      let data = {
        stroke: "equal",
        value: finalValue,
      };
      this.sy = finalValue;
      this.$emit("displayTrack", data);
    },
    remove()
    {
       this.sy = this.sy.substr(0,this.sy.length-1);
        let data = {
        stroke: "remove",
        value: this.sy,
      };
      this.$emit("displayTrack", data);
    }
  },
};
</script>

<style>
.keyboard {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  grid-row-gap: 1.2rem;
  grid-column-gap: 1rem;
  padding: 1.2rem;
}

.btn-style {
  background: white;
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  border-radius: 0.6rem;
  font-size: 30px;
  font-weight: 800;
  border-bottom: 4px solid gray;
  border-left: 3px solid gray;
  border-right: 3px solid gray;
  cursor: pointer;
}

.btn-style:active {
  border: none;
  transform: translateY(1px);
}

.equal {
  background-color: #f6a24d;
  border: 3px solid #ebe3e3;
  color: white;
}

.reset {
  background-color: red;
  border: 3px solid #ebe3e3;
  color: white;
}

.del {
  background-color: green;
  border: 3px solid #ebe3e3;
  color: white;
}
</style>
