<template>
  <div id="calculator">

    <div id="screen-container">
      <div id="screen">{{screenValue}}</div>
    </div>

    <div id="buttons-container">
      <div class="buttons">
        <span class="operator" id="clear" @click="clear">C</span>
        <span class="operator" @click="operator('division')">/</span>
        <span class="operator" @click="operator('multiplication')">x</span>
        <span @click="addNumber(7)">7</span>
        <span @click="addNumber(8)">8</span>
        <span @click="addNumber(9)">9</span>
        <span class="operator" @click="operator('subtraction')">-</span>
        <span @click="addNumber(4)">4</span>
        <span @click="addNumber(5)">5</span>
        <span @click="addNumber(6)">6</span>
        <span class="operator" @click="operator('addition')">+</span>
        <span @click="addNumber(1)">1</span>
        <span @click="addNumber(2)">2</span>
        <span @click="addNumber(3)">3</span>
        <span class="operator" id="equals" @click="equals">=</span>
        <div class="l-row">
          <span id="zero" @click="addNumber(0)">0</span>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "Calculator",
  data(){
    return {
      screenValue: 0,
      calculateValue: 0,
      operation: ""
    }
  },
  methods: {
    addNumber(number){
      if(this.screenValue === 0){
        this.screenValue = number
      } else {
				var screenString = this.screenValue.toString()
				var numberString = number.toString()
				this.screenValue = parseInt(screenString + numberString)
        // var screen = document.querySelector("#screen")
				// screen.innerText += number
				// this.screenValue = parseInt(screen.innerText)
      }
    },
    clear(){
      this.screenValue = 0
      this.calculateValue = 0
      this.operation = ""
    },
    operator(operation){
      if(this.calculateValue === 0){
        this.calculateValue = this.screenValue
        this.operation = operation
        this.screenValue = 0
      } else {
        switch(this.operation){
					case "addition":
						this.calculateValue += this.screenValue
						this.screenValue = 0
            break;
					case "subtraction":
						this.calculateValue -= this.screenValue
						this.screenValue = 0
            break;
					case "multiplication":
						this.calculateValue = this.screenValue * this.calculateValue
						this.screenValue = 0
            break;
					case "division":
						this.calculateValue = this.calculateValue / this.screenValue
						this.screenValue = 0
						break;
					default:
					this.screenValue = "ERR"
				}	
      }
    },
    equals(){
      if(this.calculateValue !== 0){
        switch(this.operation){
					case "addition":
						this.screenValue += this.calculateValue
            break;
					case "subtraction":
						this.screenValue = this.calculateValue - this.screenValue
            break;
					case "multiplication":
						this.screenValue = this.screenValue * this.calculateValue
            break;
					case "division":
						this.screenValue = this.calculateValue / this.screenValue
						break;
					default:
					this.screenValue = "ERR"
				}
				this.calculateValue = 0
      }
    }
  }
}
</script>
<style>
#calculator {
  background: #2B3D50;
  border-radius: 20px;
  padding: 15px;
  width: 335px;
  margin-left: auto;
  margin-right: auto;
}

#screen-container {
  background: #5E626D;
  border-radius: 10px;
  padding: 20px;
}

#screen {
  background: #EF5D5D;
  border: none;
  font-family: 'Orbitron', sans-serif;
  font-size: 1.4em;
  font-weight: 600;
  height: 23px;
  overflow: hidden;
  padding: 12px 15px;
  width: 265px;
  z-index: 1;
}

#zero {
  width: 225px;
}

#clear {
  background: #CF7C43;
  width: 147px;
}

#clear:active {
  background-color: #E67E22;
}

#equals {
  height: 89px;
}

#buttons-container {
  padding: 30px 0 0 15px;
}

.l-row {
  position: absolute;
  top: 354px;
}

.buttons {
  overflow: hidden;
}

.buttons span {
  background: #3383D2;
  border-radius: 3px;
  border: none;
  box-shadow: inset 0px 1px 0px #5E626D, 0px 5px 0px 0px #45637F;
  cursor: pointer;
  float: left;
  font-family: 'Oswald', sans-serif;
  width: 70px;
  height: 40px;
  margin: 0 7px 11px 0;
  line-height: 40px;
  text-align: center;
}

.buttons span:active {
  background-color: #4AA3DF;
  top: 3px;
  box-shadow: inset 0px 1px 0px #5E626D, 0px 2px 0px 0px #45637F;
}

.operator {
  font-size: 1.3em;
}
</style>
