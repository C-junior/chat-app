<template>
<nav>
    <h1>Chat App</h1>
</nav>
<div v-if="isLogin" class="login">
<Avatar :src="user.PhotoURL"/>
<button @click="signOut" > Sign Out</button>
</div>
<div v-else >
    <button @click="signIn">Sign In</button>

</div>
</template>
<script>
   import { useAuth } from '@/firebase'

   export default {
    setup() {
        const { user, isLogin, signOut, signIn } = useAuth()
        return  { user, isLogin, signOut, signIn }
    }
   }

</script>
<style scoped>
button{
    background-color: red;
    color: #000;
}
</style>