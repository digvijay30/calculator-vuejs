<template>
  <div class="calculator">
    <div class="cal-setup">
      <div class="display">
        <div class="text">{{value!==''?value:'0'}}</div>
      </div>
      <keyboard @displayTrack="updateDisplay"></keyboard>
    </div>
  </div>
</template>

<script>
import Keyboard from "./Keyboard.vue";
export default {
  components: {
    Keyboard,
  },
  data: function () {
    return {
      value: "",
    };
  },
  methods:{
      updateDisplay(data)
      {
          if(data.stroke === '')
          {
             this.value+=data.value;
          }
          else
          {
             this.value=data.value;
          }
         
      }
  }
};
</script>

<style>
.calculator {
  background: #575757;
  height: 500px;
  width: 400px;
  border-radius: 2rem;
  border-bottom: 10px solid gray;
  border-right: 10px solid gray;
  border-left: 4px solid gray;
}
.cal-setup {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  row-gap: 1.5rem;
}

.display {
  background: #bbd0bf;
  width: 100%;
  height: 80px;
  border-radius: 2rem;
  border-bottom: 6px solid #79837b;
  border-right: 4px solid #79837b;
  border-left: 4px solid #79837b;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 0.8rem;
  font-family: "digital-7", sans-serif;
  font-size: 50px;
}

.text {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: clip;
  display: flex;
  justify-content: flex-end;
}
</style>
