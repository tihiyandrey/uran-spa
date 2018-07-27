<template>
  <div id="app">
    <header>  
         
    </header>
    <main>      
      <router-view v-if="state == 'login'" @albumPage="albumPage"></router-view>
      <Album v-else-if="state == 'album'"></Album>
      <Album v-else>Error</Album>
    </main>
  </div>
</template>

<script>
export default {
  data() {
  	return {
  		state: 'login'
  	}
  },
  methods: {
  	albumPage() {
  		this.state = 'album';
  	}
  }
}
</script>

<style>

</style>
