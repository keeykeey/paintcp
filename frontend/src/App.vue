<template>
  <div id="app">
    <p>
      Paint as you feel
    </p>
    <selector
      :defaultVal = "fontSize"
      :selectEl = "setFontSize"
      :optionList = "fontSizeList"
    />
    <paint-pallet
      :color = "fontColor"
      :fontSize  = "fontSize"
    />
    <div>
      <label>出力形式 </label>
      <input type="radio" value="0" v-model="radioVal"/>
      <label>png </label>
      <input type="radio" value="1" v-model="radioVal"/>
      <label>jpeg </label>
      <input type="radio" value="2" v-model="radioVal"/>
      <label>svg </label>
    </div>
    <p>
      出力形式 : {{ radioVal }}
    </p>
  </div>
</template>

<script>
import PaintPallet from './components/PaintPallet'
import Selector from "./components/Selector"
const DEFAULT_FONT_SIZE = "3"

export default {
  name: 'App',
  components: { 
    PaintPallet,
    Selector
  },
  data: function(){
    return{
      fontColor: "#40a174",
      fontSize: DEFAULT_FONT_SIZE,
      fontSizeList: [1,2,3,4,5,6,7,8,9,10],
      radioVal: "0",
    }
  },
  watch: {
    radioVal: function(val) {
      // TODO //
      console.log("watch val",val);
    }
  },
  methods: {
    setColor(color) {
      this.color = color;
    },
    setFontSize(size) {
      this.fontSize = String(size);
    },
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 20px;
}
</style>
