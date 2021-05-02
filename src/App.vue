<template>
    <div id='case'>
      <div id='displayPart'>
        <span id='logPart'>{{calculLog}}</span><hr/>
        <span id='mainPart'>{{firstNum}}</span>
      </div>
      <div id='buttonPart'>
        <table>
          <tr>
            <td><button v-on:click="conversion('2')"><span id='text-b'>2진수</span></button></td>
            <td><button v-on:click="conversion('8')"><span id='text-b'>8진수</span></button></td>
            <td><button v-on:click="conversion('16')"><span id='text-b'>16진수</span></button></td>
            <td><button v-on:click="clear()"><span>CE</span></button></td>
          </tr>
          <tr>
            <td><button v-on:click="addNum('7')"><span>7</span></button></td>
            <td><button v-on:click="addNum('8')"><span>8</span></button></td>
            <td><button v-on:click="addNum('9')"><span>9</span></button></td>
            <td><button v-on:click="operat('/')"><span>/</span></button></td>
          </tr>
          <tr>
            <td><button v-on:click="addNum('4')"><span>4</span></button></td>
            <td><button v-on:click="addNum('5')"><span>5</span></button></td>
            <td><button v-on:click="addNum('6')"><span>6</span></button></td>
            <td><button v-on:click="operat('*')"><span>*</span></button></td>
          </tr>
          <tr>
            <td><button v-on:click="addNum('1')"><span>1</span></button></td>
            <td><button v-on:click="addNum('2')"><span>2</span></button></td>
            <td><button v-on:click="addNum('3')"><span>3</span></button></td>
            <td><button v-on:click="operat('-')"><span>-</span></button></td>
          </tr>
          <tr>
            <td><button v-on:click="addNum('.')"><span>.</span></button></td>
            <td><button v-on:click="addNum('0')"><span>0</span></button></td>
            <td><button v-on:click="calcul()"><span>=</span></button></td>
            <td><button v-on:click="operat('+')"><span>+</span></button></td>
          </tr>
        </table>
      </div>
    </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      firstNum:'0',
      secondNum:'0',
      operator:'null',
      calculLog:'null'
    }
  },
  methods: {
    addNum(num){
      if(this.firstNum == '0'){
        this.firstNum = num;
      }
      else{
        this.firstNum += num;
      }
    },
    clear(){
      this.firstNum = '0';
      this.secondNum = '0';
      this.calculLog = 'null';
    },
    operat(o){
      if(this.firstNum == '0'){
        this.operator = 'null';
      }
      else{
        this.operator = o;
        this.secondNum = this.firstNum;
        this.calculLog = this.firstNum + o;
        this.firstNum = '0';
      }
    },
    calcul(){
      switch(this.operator){
        case '+':{
          let a = Number(this.secondNum);
          let b = Number(this.firstNum);
          this.calculLog = this.calculLog+this.firstNum;
          this.firstNum = a+b;
          break;
        }
        case '-':{
          let a = Number(this.secondNum);
          let b = Number(this.firstNum);
          this.calculLog = this.calculLog+this.firstNum;
          this.firstNum = a-b;
          break;
        }
        case '/':{
          let a = Number(this.secondNum);
          let b = Number(this.firstNum);
          this.calculLog = this.calculLog+this.firstNum;
          this.firstNum = a/b;
          break;
        } 
        case '*':{
          let a = Number(this.secondNum);
          let b = Number(this.firstNum);
          this.calculLog = this.calculLog+this.firstNum;
          this.firstNum = a*b;
          break;
        }
      }
    },
    conversion(s){
      if(s=='2'){
        this.calculLog = this.firstNum;
        let a = Number(this.firstNum);
        this.firstNum = a.toString(2);
      }
      if(s=='8'){
        this.calculLog = this.firstNum;
        let a = Number(this.firstNum);
        this.firstNum = a.toString(8);
      }
      if(s=='16'){
        this.calculLog = this.firstNum;
        let a = Number(this.firstNum);
        this.firstNum = a.toString(16);
      }
    }
  }
} 
</script>

<style>
@font-face {
    font-family: 'DOSSaemmul';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_eight@1.0/DOSSaemmul.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}
html{width:100%; height: 100%; font-size: 0; font-family: DOSSaemmul; background-image:"../assets/back.png";}
#case{width: 300px; height: 450px; background-color: black; border-radius: 5%; border:thick double white;}
#displayPart{width: 240px; height: 80px; text-align: right; margin:10px 15px; padding: 10px; border-radius: 2.5%;
border:thick double black; background-color: white;}
hr{border: 0; height: 3px; background-color: black;}
#logPart{font-size: 15px;}
#mainPart{font-size: 70px;}
#buttonPart{width: 260px; height: 300px; margin:10px 15px; border-radius: 2.5%; border:thick double black;
background-color: white;}
table{width: 100%; border-collapse: collapse; border-spacing: 0px; table-layout: fixed;}
tr{width: 100%; border: 0; padding: 0;}
td{padding: 0;}
button{width: 100%; height: 60px; margin: 0; border:thick double black; background-color: white;}
#text-b{font-size: 14px;}
span{font-family: DOSSaemmul; font-size: 20px; padding: 0;}

</style>
