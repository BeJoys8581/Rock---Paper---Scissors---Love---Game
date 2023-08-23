<script setup>
 import { ref, computed } from 'vue'
 
 const random = ['ค้อน', 'กระดาษ', 'กรรไกร', 'ความรัก'];
 const botRandom = ref("");
 const playerRandom = ref("");
 const losses = ref(0);
 const wins = ref(0);
 const draws = ref(0);
 
 function play(){
  botRandom.value = random[Math.floor(Math.random() * random.length)];
  playerRandom.value = random[Math.floor(Math.random() * random.length)];

  if (
    (botRandom.value === 'ค้อน' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'กระดาษ' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'กรรไกร' && playerRandom.value === 'กระดาษ') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กระดาษ')
  ) {
    losses.value++;
  } else if (
    botRandom.value === playerRandom.value
  ) {
    draws.value++;
  } else {
    wins.value++;
  }
}
 
function resetValues(){
   botRandom.value = "";
   playerRandom.value = "";
   losses.value = 0;
   wins.value = 0;
   draws.value = 0;
 };

 function RanImg(pic) {
  const romImgs = {
    'ค้อน':    "https://www.nicepng.com/png/detail/6-61708_rock-rock-paper-scissors-clipart.png",
    'กระดาษ': "https://www.pngkey.com/png/detail/816-8161571_transparent-rock-paper-scissors-png.png",
    'กรรไกร': "https://www.seekpng.com/png/detail/111-1114370_rock-paper-scissors-rock-paper-scissors-clipart.png",
    'ความรัก' : "data:image/png;base64,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" ,
  };
  return romImgs[pic];
}

const winPercentage = computed(() => {
    const total = wins.value + draws.value + losses.value
    return total ? (wins.value / total) * 100 : 0
  })



 </script>
 
 <template>
  
  <div>
    <header class="container">
      <h1 class="">Rock , Paper , Scissors , Love</h1>
    </header>
    <p>( love conquers everything •◦❤◦• )</p>
    <div class="container">

      <div class="playerbox">
        <p style="color: rgb(17, 255, 0);">Player (ﾉ&gt;｡&lt;)ﾉ </p>  <br>
        <img class="imgsize" :src="RanImg(playerRandom)"/><br>
        {{ playerRandom }} <br>
      </div>

      &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp;
      
      <h1 style="color: blue;">VS</h1>

      &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp;

      <div class="botbox">
        <p style="color: red;"> Bot Ψ(｀_ ´)ﾉ </p> <br>
        <img class="imgsize" :src="RanImg(botRandom)"/><br>
        {{ botRandom }}   
      </div> 
      
        <br>
    </div>


    <div>
        <span class="font-bold">Wins : </span> {{ wins }}   |
        <span class="font-bold">Draws : </span> {{ draws }}  |
        <span class="font-bold">Losses :</span> {{ losses }} 
      </div>

      <div class="text-lg">
        Wins Rates : {{ Math.round(winPercentage) }}%
      </div>
      
      <br>


    <button @click="play" 
                class="button">
                เป่ายิ๊งงงงงงงงงงงงงงงงงง ฉุ๊บบบบ

        </button>

        &nbsp;&nbsp;&nbsp;

        <button @click="resetValues" class="button1"> เริ่มใหม่ </button>

      </div>

</template>

<style scoped>
.imgsize{
 width: 300px;
 height: 300px;
 border-width: none;
 border-radius: 45px;
}

.container{
  display: flex;
}

.botbox{
} 

.playbox{

}

h1{
  font-size: 70px;
  margin: auto;
}

.start{
  background-color: greenyellow;
}

.restart{
  background-color: red;
}

.button {
padding: 15px 25px;
  font-size: 24px;
  text-align: center;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #04AA6D;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #999;
}

.button:hover {background-color: #3e8e41}

.button:active {
  background-color: #3e8e41;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

.button1 {
padding: 15px 25px;
  font-size: 24px;
  text-align: center;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #ff0000;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #999;
}

.button1:hover {background-color: #c22d2d}

.button1:active {
  background-color: #8e0f0f;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

.font-bold{
  font-weight: bold;
}

</style>