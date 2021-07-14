<template>
    <div id="battery-app">
     <!-- <div style="flex-direction: row;display: flex">
        <div class="main-div" :style="borderStyle">

          <div class="low" :style="customStyleLow"></div>

          <div class="medium" :style="customStyleMedium"></div>

          <div class="medium-one" :style="customStyleMedium1"></div>

          <div class="high" :style="customStyleHigh"></div>

          <div class="high-one" :style="customStyleHigh1"></div>

          <img src="../src/img/thunderRed.png" class="thunderRed" :style="customImg">
          <img src="../src/img/thunderYellow.png" class="thunderYellow" :style="customImgY">
          <img src="../src/img/thunderGreen.png" class="thunderGreen" :style="customImgG">
        </div>
        <div class="last-div" :style="{backgroundColor : color}">

        </div>

      </div>
      <div>
        <button @click="openCharge">Open Charge</button>
        <button @click="changeLow">+1</button>
        <button @click="changeMedium">+2</button>
        <button @click="changeMedium1">+3</button>
        <button @click="changeHigh">+4</button>
        <button @click="changeHigh1">+5</button>
      </div>-->





      <div style="flex-direction: row;display: flex">
        <div class="main-div" :style="borderStyle">

          <div class="low"  :style="[chargeStyle, {display : displayDivR}]"></div>

          <div class="medium" :style="[chargeStyle, {display : displayDivY}]"></div>

          <div class="medium-one" :style="[chargeStyle, {display: displayDivY1}]"></div>

          <div class="high" :style="[chargeStyle, {display: displayDivG}]"></div>

          <div class="high-one" :style="[chargeStyle, {display : displayDivG1}]"></div>

          <img src="../src/img/thunderRed.png" class="thunderRed" :style={display:displayCharge}>
          <img src="../src/img/thunderYellow.png" class="thunderYellow" :style={display:displayChargeM}>
          <img src="../src/img/thunderGreen.png" class="thunderGreen" :style={display:displayChargeH}>
        </div>
        <div class="last-div" :style="{backgroundColor : color}">

        </div>

      </div>
      <div style="margin-top: 20px">
        <button @click="openCharge">Toogle Charge</button>
        <input type="range" min="0" max="100" step="1" v-model="value">

      </div>



    </div>
</template>

<script>


export default {


  data : function (){
    return {
      color : 'red',
      colorBorder : 'red',
      displayM : 'none',
      displayH : 'none',
      displayCharge : 'none',
      displayChargeM : 'none',
      displayChargeH : 'none',
      displayDivR : 'none',
      displayDivY : 'none',
      displayDivY1 : 'none',
      displayDivG : 'none',
      displayDivG1 : 'none',
      value : 0
    }
  },
  computed : {

    chargeStyle : function (){
      if(this.value == 0){
        this.displayChargeH = 'none'
        this.displayCharge = 'none'
        this.displayChargeM = 'none'
      }
      if(this.value >=1 && this.value < 20){
        this.displayDivR = 'block'
        this.displayDivY = 'none'
        this.displayDivY1 = 'none'
        this.displayDivG = 'none'
        this.displayDivG1 = 'none'
        this.color ='#FF0000'
        this.displayChargeH = 'none'
        this.displayCharge = 'block'
        this.displayChargeM = 'none'
        return{
          backgroundColor: '#FF0000'

        }
      }
      if(this.value >= 20 && this.value < 40){
        this.displayDivR = 'block'
        this.displayDivY = 'block'
        this.displayDivY1 = 'none'
        this.displayDivG = 'none'
        this.displayDivG1 = 'none'
        this.color = '#FFE700'
        this.displayChargeH = 'none'
        this.displayCharge = 'none'
        this.displayChargeM = 'block'
        return{
          backgroundColor: '#FFE700'

        }
      }
      if(this.value >= 40 && this.value < 60){
        this.displayDivR = 'block'
        this.displayDivY = 'block'
        this.displayDivY1 = 'block'
        this.displayDivG = 'none'
        this.displayDivG1 = 'none'
        this.displayChargeH = 'none'
        this.displayCharge = 'none'
        this.displayChargeM = 'block'
        this.color ='#FFE700'
        return{
          backgroundColor: '#FFE700'

        }
      }
      if(this.value >= 60 && this.value < 80){
        this.displayDivR = 'block'
        this.displayDivY = 'block'
        this.displayDivY1 = 'block'
        this.displayDivG = 'block'
        this.displayDivG1 = 'none'
        this.color ='#418F19'
        this.displayChargeH = 'block'
        this.displayCharge = 'none'
        this.displayChargeM = 'none'
        return{
          backgroundColor: '#418F19'

        }
      }
      if(this.value >= 80 && this.value <= 100){
        this.displayDivR = 'block'
        this.displayDivY = 'block'
        this.displayDivY1 = 'block'
        this.displayDivG = 'block'
        this.displayDivG1 = 'block'
        this.color ='#418F19'
        return{
          backgroundColor: '#418F19'

        }
      }
    },

    borderStyle : function (){
      return {
        border : 5+"px solid "+this.color,
      }
    }
  },
  methods : {
    openCharge : function (){
      this.displayCharge = 'block'
    }
  }
}
</script>

<style scoped>
#battery-app{
  width: min-content;
  height: 500px;
  margin-right: auto;
  margin-left: auto;

}
.main-div{
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 10px;
  border: 5px solid green;
  border-radius: 10px;
  padding: 5px 2px;
  width: 300px;
  height: 100px;
  flex-direction: row;
  display: flex;
}

.low{
  height: 100px;
  width: 50px;
  margin-left: 5px;
  margin-right: 3px;
  display: block;
}

.last-div{
  width: 25px;
  height: 60px;
  border-top-right-radius: 50%;
  border-bottom-right-radius: 50%;
  background-color: red;
  margin-top: 30px;
  margin-left: 3px;
  opacity: 75%;
}

.thunderRed{
  top:110px;
  width: 100px;
  height:150px;
  position: absolute;
  left: 580px;
  display: none;
}
.thunderYellow{
  top:110px;
  width: 100px;
  height:150px;
  position: absolute;
  left: 580px;
  display: none;
}
.thunderGreen{
  top:110px;
  width: 100px;
  height:150px;
  position: absolute;
  left: 580px;
  display: none;
}
.medium{
  height: 100px;
  width: 50px;
  margin-left: 5px;
  margin-right: 5px;
  display: block;
}
.medium-one{
  height: 100px;
  width: 50px;
  margin-left: 5px;
  margin-right: 5px;
  display: block;
}
.high{
  height: 100px;
  width: 50px;
  margin-left: 5px;
  margin-right: 5px;
  display: block;
}
.high-one{
  height: 100px;
  width: 50px;
  margin-left: 5px;
  margin-right: 5px;
  display: block;
}
</style>
