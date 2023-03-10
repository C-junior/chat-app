<template>

  
  <NavC/>
  <!-- <CardColect/> -->
  <ChatC/>
  
</template>

<script>
//import CardColect from './components/CardColect.vue'
import NavC from './components/NavC.vue'
import ChatC from '../src/components/ChatC.vue'

export default {
  name: 'App',
  components: {
    NavC, 
    ChatC,
    //CardColect
  }
}

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #49749e;
  margin-top: 60px;
  background-color: #091622;
}
</style>
