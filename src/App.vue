<template>
  <div v-bind:class="{default:classp,second:ente}">
    <div >

    
  <button @click="ente=!ente">Change Background</button>  
    <h1  class="heading">Roll nd Dice</h1>
 </div>



<div class="imgss">
  <h3 v-if="start" @click="startGame">Start game</h3>
   <img :src="imgs" :style="st" @click="genRandom">
 </div>

<p v-if="user >=50" class="score" >You Win game {{user}} </p>
<p v-if="system >= 50" class="score">Sytem  Won the game {{system}}</p>


<div class="content" v-if="!start">
  <h2>Player Score : {{user}}</h2>
  <h2>System Score : {{system}} </h2>
</div>




<button @click="genRandom" v-if="!start" class="btn">Roll Dice</button>
<button @click="resetGame"  v-if="!start" >Restart</button>

  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      classp: true,
      ente: false,
      start: true,
      imgs: "",
      user: 0,
      system: 0,
      st: ""
    };
  },
  methods: {
    genRandom() {
      if (this.system >= 50) {
      
        alert("Sytem won game" + " " + this.system);
        this.system = 0;
        this.user = 0;
        this.resetGame();
        return;
      }
      if (this.user >= 50) {
       
        alert("You won game" + " " + this.user);
        this.user = 0;
        this.system = 0;
        this.resetGame();

        return;
      }

      let snd = new Audio('../audio/ONEDICE.WAV')
      snd.play()
      let num = Math.floor(Math.random() * 6) + 1;

      switch (num) {
        case 1:
          this.imgs = "../images/1.png";
          this.st = {
            border: "4px doubled #1abc9c"
          };
          this.user += num;

          break;
        case 2:
          this.imgs = "../images/2.png";
          this.user += num;
          this.st = {
            border: "4px dotted #2ecc71"
          };
          break;

        case 3:
          this.imgs = "../images/3.png";
          this.user += num;
          this.st = {
            border: "4px dotted #3498db"
          };
          break;

        case 4:
          this.imgs = "../images/4.png";
          this.user += num;
          this.st = {
            border: "4px dotted rgba(239, 87, 119,1.0)"
          };
          break;

        case 5:
          this.imgs = "../images/5.png";
          this.user += num;
          this.st = {
            border: "4px dotted #e74c3c"
          };
          break;

        case 6:
          this.imgs = "../images/6.png";
          this.user += num;
          this.st = {
            border: "4px dotted #ecf0f1"
          };
          break;
      }
      this.SytemRandom();
    },
    SytemRandom() {
      let num = Math.floor(Math.random() * 6) + 1;

      switch (num) {
        case 1:
         
          this.system += num;

          break;
        case 2:
         
          this.system += num;
         
          break;

        case 3:
          
          this.system += num;
       
          break;

        case 4:
         
          this.system += num;
          
          break;

        case 5:
         
          this.system += num;
         
          break;

        case 6:
          
          this.system += num;
          
          break;
      }
    },
    resetGame() {
      this.system = 0;
      this.user = 0;
      this.imgs = null;
      this.st = null;
      this.start = true;
    },
    startGame() {
      this.start = false;
      this.system = 0;
      this.user = 0;
      this.genRandom();
    }
  },
  created() {
    
    this.resetGame();
  }
};
</script>

<style>
*,
*::after,
*::before {
  box-sizing: border-box;
}


button {
  padding: 0.7rem;
  background-color: rgb(9, 10, 5);
  border-radius: 11px;
  font-size: 1rem;
  color: rgb(219, 221, 223);
  outline: none;
  box-shadow: inset 20px 2px 20px 0px #a51717;
  transition: all 0.3s;
  margin-right: 1rem;
}

button:hover {
  box-shadow: inset 20px 2px 20px 0px transparent;
  background-color: #a51717;
}

.default {
  color: #f4f4f4;
  background-image: linear-gradient(black,#6d6d19);
  padding: 2rem;
  text-align: center;
  box-shadow: inset -2px 1px 20px 5px black;
  font-family: cursive;
  height: 100vh;
  text-transform: capitalize;
  border: 2px solid whitesmoke;
}

.default h1{
  
   color: rgb(221, 202, 32);
   text-align: left;

}

.second {
  color: white;
 background-image: linear-gradient(black,#907f4f);
  padding: 2rem;
  position: relative;
  font-family: cursive;
  height: 100vh;
  text-transform: capitalize;
}

.second h1{
  text-align: right;
   color:yellow; 

}

.imgss {
  box-shadow: -20px 10px 2px 0px rgb(219, 221, 223);
  border: 2.9px double rgba(243, 241, 241, 0.712);
  border-radius: 20px;
  padding: 1rem 1rem 1rem 1rem;
  backface-visibility: hidden;
  background-color: rgba(5, 12, 10, 0.57);
  width: 10rem;
  height: 170px;
  margin: 0 auto;
  transition: all 0.3s;
  z-index: 100;
  cursor: pointer;
}

img {
  border-radius: 20px;
  box-shadow: 2px 10px 10px black;
  transition: all 0.3s;
}

.imgss:hover {
  box-shadow: none;
}

.imgss:hover > img {
  box-shadow: 0px 7px 10px #fff;
  padding: 2px;
}

.score {
  background-color: #dfff;
  color: rgb(54, 48, 48);
  width: fit-content;
  padding: 1rem;
  text-align: center;
  margin:2rem auto;

}

.content {
  margin-top: 10rem;
}

h3 {
  cursor: pointer;
  text-transform: capitalize;
  transition: all 0.3s;
}
h3:hover {
  color: rgb(143, 151, 153);
}
</style>
