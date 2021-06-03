<template>
<div>
  <a href="#">  
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        CALCULATOR
  </a>

  <div class="calculator">
    
    <div class="display "> {{current || '0'}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click ="divide" class="btn operator">/</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">X</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn" id="zero">0</div>
    <div @click="append('.')" class="btn">.</div>
    <div @click="equal" class="btn operator trans">=</div>
  </div>
  </div>
</template>

<script>
  export default {
    
    data(){
      return{
        previous: null,
        current:'',
        operator: null,
        operatorClicked: false
      }
    },
    methods: {
      clear() {
        this.current= '';
      },
      sign() {
          this.current = this.current.charAt(0) === '-' ?
          this.current.slice(1) : `-${this.current}`;
      },
      percent(){
        this.current = `${parseFloat(this.current) / 100}`;
      },
      append(number) {
         if (this.operatorClicked){
           this.current = '';
           this.operatorClicked= false;
         }
         this.current = this.current + number;
      },
      setPrevious(){
        this.previous = this.current;
        this. operatorClicked = true;
      },
      divide(){
        this.operator = (a, b) => a / b;
        this.setPrevious();      
      },
       times(){
        this.operator = (a,b) => a*b;
        this.setPrevious();      
    },
    minus(){
        this.operator = (a,b) => a-b;
        this.setPrevious();      
    },
      add(){
        this.operator = (a,b) => a+b;
        this.setPrevious();     
    },
    equal(){
      this.current =  `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;

         }
    }
 }

</script>

<style>
*{
  background: #000;
}
a{
  position: absolute;
  top:15%;
  left:55%;
  font-size:30px;
  font-weight:bold;
  font-family:sans-serif;
  transform: translate(-50%,-50%);
  padding:30px 60px;
  letter-spacing:2px;
  text-decoration:none;
  box-shadow:0 20px 50px rgba(0, 0, 0, .5);
  overflow:hidden;
  color:rgb(9, 13, 226);
 

}
a::before{
  content:'';
  position:absolute;
  top: 2px;
  left:2px;
  bottom:2px;
  width:50%;
  background:rgba(255, 255, 255, 0.05);
}
 a span:nth-child(1){

  position: absolute;
  top:0;
  left:0;
  width: 100%;
  height:2px;
  background:linear-gradient(to right, #0c002b, #1779ff);
  animation: animate1 2s linear infinite;
   animation-delay:1s;
 }
@keyframes animate1{
  0%{
    transform: translateX(-100%);
  }
  100%{
    transform: translateX(100%);
  }
}
 a span:nth-child(2){
  position: absolute;
  top:0;
  right:0;
  width: 2px;
  height:100%;
  background:linear-gradient(to bottom, #0c002b, #1779ff);
  animation: animate2 2s linear infinite;
}
@keyframes animate2{
  0%{
    transform: translateY(-100%);
  }
  100%{
    transform: translateY(100%);
  }
}
a span:nth-child(3){
  position: absolute;
  bottom:0;
  left:0;
  width: 100%;
  height:2px;
  background:linear-gradient(to left, #0c002b, #1779ff);
animation: animate3 2s linear infinite;
}
@keyframes animate3{
  0%{
    transform: translateX(100%);
  }
  100%{
    transform: translateX(-100%);
  }
}
a span:nth-child(4){
  position: absolute;
  top:0;
  left:0;
  width: 2px;
  height:100%;
  background:linear-gradient(to top, #0c002b, #1779ff);
  animation-delay:1s;
  animation: animate4 2s linear infinite;
   animation-delay:1s;
}
@keyframes animate4{
  0%{
    transform: translateY(100%);
  }
  100%{
    transform: translateY(-100%);
  }
}

.calculator{
  margin-left:25%;
  width:400px;
  padding:25px;
  font-size:2em;
  display: grid;
  margin-top:150px;
  font-weight:bold;
  font-family: Helvetika cursive;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display{
  grid-column: 1 / 5;
  background:#eee;
  height:60px;
  margin:5px;
  margin-top:50px;
  text-align:center;
  
}
.btn{
  margin:5px;
  background-image:linear-gradient(rgb(223, 48, 48), tomato);
  animation: animate 3s linear infinite; 
  font-family: italic;
  box-shadow: 0 20px 50px rgb(61, 41, 41)
  
}

.btn:hover{
  color:white;
  background:rgb(255, 78, 46);
  border: 0.3px solid gray;
}
div:nth-child(1)
{
  animation-delay:0s;
}
div:nth-child(2)
{
  animation-delay:0.25s;
}
div:nth-child(3)
{
  animation-delay:0.50;
}
div:nth-child(4)
{
  animation-delay:0.75s;
}
div:nth-child(5)
{
  animation-delay:1s;
}
div:nth-child(6)
{
  animation-delay:1.25s;
}

div:nth-child(7)
{
  animation-delay:1.5s;
}
div:nth-child(8)
{
  animation-delay:1.75s;
}

div:nth-child(9)
{
  animation-delay:2s;
}
div:nth-child(10)
{
  animation-delay:2.22s;
}
div:nth-child(11)
{
  animation-delay:2.75s;
}
div:nth-child(12)
{
  animation-delay:3s;
}
div:nth-child(13)
{
  animation-delay:3.25s;
}
div:nth-child(14)
{
  animation-delay:3.5s;
}
div:nth-child(15)
{
  animation-delay:3.75s;
}
div:nth-child(16)
{
  animation-delay:4s;
}
div:nth-child(17)
{
  animation-delay:4.25s;
}
div:nth-child(18)
{
  animation-delay:4.5s;
}
div:nth-child(19)
{
  animation-delay:4.75s;
}
div:nth-child(20)
{
  animation-delay:5s;
}
div:nth-child(1)
{
  animation-delay:0s;
}




@keyframes animate{
  0%,100%
  {
    color: #fff;
    filter: blur(2px);
    box-shadow: 0 0010px #1ec041,
                0 0010px#1ec041
                0 0020px #1ec041,
                0 0040px #1ec041,
                0 0080px #1ec041,
                0 00120px #1ec041,
                0 00200px #1ec041,
                0 00300px #1ec041
                0 00400px #1ec041,
                0 00500px #1ec041,
                0 00600px #1ec041,
                0 00700px #1ec041,
                0 00800px #1ec041,
                0 00900px #1ec041,
                0 001000px #1ec041,
  }
   5%,95%
  {
    color: #111;
    filter: blur(0px);
    text-shadow:  none;
  }
}


#zero{
  grid-column:1 / 3;
}

</style>