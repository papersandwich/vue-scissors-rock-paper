<template>
  <div id="container">
    <div id="bot-placeholder">
      <img :src="botImage">
    </div>
    <div id="you-placeholder">
      <img src="/images/Placeholder-You.png">
    </div>
    <div>{{ botChoice }} / {{ userChoice }} || {{ winner }}</div>
    <div id="buttons-container">
      <div id="btn-paper" @click="userPicked('p');botPicked();computeWinner()"></div>
      <div id="btn-scissor" @click="userPicked('s');botPicked()"></div>
      <div id="btn-rock" @click="userPicked('r');botPicked()"></div>
    </div>
  </div>
</template>
 
<script>
export default {
  name: 'App',
  data() {
    return {
      botChoice: '',
      userChoice: '',
      botPlaceHodlerImage: '',
      youPlaceHodlerImage: '',
      winner: null, //bot, player
    }
  },
  methods: {
    userPicked(userPicked){
      console.log('userPicked:'+userPicked);
      this.userChoice = userPicked;
    },
    botPicked(){
      const randomNumber = Math.floor(Math.random() * 3) + 1;
      let result = '';
      if (randomNumber === 1) {
        result = 'r'; // 1 對應 'r'
      } else if (randomNumber === 2) {
        result = 'p'; // 2 對應 'p'
      } else if (randomNumber === 3) {
        result = 's'; // 3 對應 's'
      }

      console.log('botPicked:'+result);
      this.botChoice = result;
    },
    computeWinner(){
      console.log(`${this.botChoice} ${this.userChoice}`)
      if(this.botChoice === this.userChoice){
        this.winner = null;
      }
      else if(this.botChoice === 'r'){
        this.winner = (this.userChoice === 'p') ? 'player' : 'bot';
      }
      else if(this.botChoice === 'p'){
        this.winner = (this.userChoice === 's') ? 'player' : 'bot';
      }
      else if(this.botChoice === 's'){
        this.winner = (this.userChoice === 'r') ? 'player' : 'bot';
      }
      console.log(`${this.botChoice} ${this.userChoice} ${this.winner}`)
    },
    translateResult(input){
      let output = '';
      return output;
    }
  },
  computed:{
    botImage() {
      console.log('inside botImage()');
      if(winner == null){
        
      }
      return '/images/Placeholder-Bot.png';
    },
    playerImage() {
      return '/images/Placeholder-You.png';
    },
  }
}

</script>
 
<style>
#container {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  padding-top: 40px;
  box-sizing: border-box;
  background-color: #44D7B6;
}
 
#bot-placeholder, #you-placeholder {
  flex: 0px 2 1;
}
 
#bot-placeholder img, #you-placeholder img {
  display: block;
  width: 60%;
  height: auto;
  margin: auto;
}
 
#buttons-container {
  flex: 0px 1 1;
  display: flex;
  flex-direction: row;
}
 
#buttons-container div {
  flex: 0px 1 1;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center bottom;
}
 
#buttons-container div#btn-paper {
  background-image: url('/public/images/paper-btn.png');
}
 
#buttons-container div#btn-scissor {
  background-image: url('/public/images/scissor-btn.png');
}
 
#buttons-container div#btn-rock {
  background-image: url('/public/images/rock-btn.png');
}
</style>