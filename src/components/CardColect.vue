<template>
    <div>
      <button @click="dropItems">Drop</button>
      <div v-for="(item, index) in items" :key="index">
        <button :disabled="!isOptionEnabled(item)" @click="addItem(item)">
          {{ item.name }}
        </button>
      </div>
      <div>Inventory:</div>
      <ul>
        <li v-for="(item, index) in inventory" :key="index">
          <img :src=item.img alt="">
          <br>
          {{ item.name }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  import { ref, reactive } from 'vue'
  
  export default {
    setup() {
      const items = ref([])
      const inventory = reactive([])
      const selectedItems = ref([])
  
      const addItem = item => {
        inventory.push(item)
        selectedItems.value.push(item)
      }
  
      const isOptionEnabled = item => {
        return !selectedItems.value.includes(item)
      }
  
      const dropItems = () => {
        selectedItems.value = []
        const randomItems = getRandomItems()
        items.value = randomItems
      }
  
      const getRandomItems = () => {
        // replace this with your own data source
        const data = [
      { id: 1, name: 'Sword', description: 'A sharp sword for combat', img:'https://static.wikia.nocookie.net/food-fantasy/images/f/f5/Basic-Ratatouille.png'},
      { id: 2, name: 'Potion', description: 'A magical potion for healing', img:'https://static.wikia.nocookie.net/food-fantasy/images/e/e0/Basic-Escargot.png' },
      { id: 3, name: 'Bow', description: 'A sturdy bow for archery', img:'https://i.pinimg.com/originals/57/41/6c/57416cf1b3191ed529e18404a8730845.png' },
      { id: 4, name: 'Shield', description: 'A strong shield for defense', img:'https://i.pinimg.com/originals/cd/4d/d9/cd4dd9a90b618315f4b07b53ba51dc97.png' },
      { id: 5, name: 'Wand', description: 'A magical wand for casting spells', img:'https://i.pinimg.com/736x/81/7c/23/817c23af3349369338fc39bb4ad1dd82.jpg' }   
   
        ]
  
        const randomItems = []
        while (randomItems.length < 3) {
          const index = Math.floor(Math.random() * data.length)
          const item = data[index]
          if (!randomItems.includes(item)) {
            randomItems.push(item)
          }
        }
  
        return randomItems
      }
  
      return {
        items,
        inventory,
        addItem,
        isOptionEnabled,
        dropItems,
      }
    },
  }
  </script>