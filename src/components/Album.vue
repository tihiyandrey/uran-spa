<template>
<div class="container">
  <div class="row justify-content-center align-items-center">
    <div class="col-md">Hi, <span id="name"></span> </div>
  </div>
</div>
</template>

<script>
  export default {
    methods:{
        startHi: function() {
          FB.api('/me', { fields: 'name,email' }, function(profile) {
            //alert (profile.name);   
            document.getElementById('name').innerHTML = profile.name;     
          });
        }
    },
    created: function(){
        this.startHi()
    }
  }
</script>
<style scoped>

</style>
