<template>
<div class="main">
  <h1>Leave a reaction:</h1>
  <!-- skrive navn -->
  <input v-model="current_user" placeholder="your name here">

  <!-- ikonene og tallene under -->
  <div class="container">
    <div class="emoji"><img class="Icon" :src="image1" alt="Emoji icon" @click="emojiNumber++, add_user()"></div>
    <div class="heart"><img class="Icon" :src="image2" alt="Heart icon" @click="heartNumber++, add_user()"></div>
    <div class="uparrow"><img class="Icon" :src="image3" alt="Arrow up icon" @click="uparrowNumber++, add_user()"></div>
    <div class="downarrow"><img class="Icon" :src="image4" alt="Arrow down icon" @click="downarrowNumber++, add_user()"></div>
    <div class="heartNumber"><p>{{heartNumber}}</p></div>
    <div class="emojiNumber"><p>{{emojiNumber}}</p></div>
    <div class="uparrowNumber"><p>{{uparrowNumber}}</p></div>    
    <div class="downarrowNumber"><p>{{downarrowNumber}}</p></div>
  </div>

  <!-- liste med nyeste reaksjoner-->
  <h2 class="lastReactions">Last Reactions</h2>
  <p class="names" v-for="user in users">
    {{user.name}}
  </p>
</div>
</template>

<script>
// importere users.json
import userData from './assets/users.json'
export default {
  data: function(){
    return {
      // variabler
      users: userData,
      image1: 'src/assets/images/happy.png',
      image2: 'src/assets/images/heart.png',
      image3: 'src/assets/images/up-arrow.png',
      image4: 'src/assets/images/down-arrow.png',
      emojiNumber: 0,
      heartNumber: 0,
      uparrowNumber: 0,
      downarrowNumber: 0,
      current_user: ''
    }
  },
  methods: {
    // funksjon
    add_user(){
      this.users.unshift({
        "id": "new",
        "name": this.current_user
      })
      // behold de 4 siste navn
      this.users.length = 4;
    },
  }
}
</script>

<style scoped>
</style>