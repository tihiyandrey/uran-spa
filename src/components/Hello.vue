<template>
  <div id="new">
    <div class="container">
      <div class="login-block row justify-content-center align-items-center">
        <div class="col-md-3">
          <div class="inner cover">
            <h5 class="text-center mb-5">App Login</h5>
            <button type="button" class="btn btn-primary btn-block" @click="openFbLoginDialog">Facebook Login</button>              
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  window.fbAsyncInit = function() {
    FB.init({
      appId      : '228210221137701',
      cookie     : true, 
      xfbml      : true,
      version    : 'v3.0'
    });
    FB.getLoginStatus(function(response) {
      
    });

  };
  (function(d, s, id) {
    var js, fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s); js.id = id;
    js.src = "https://connect.facebook.net/en_US/sdk.js";
    fjs.parentNode.insertBefore(js, fjs);
  }(document, 'script', 'facebook-jssdk'));

  export default {
    methods: {
    openFbLoginDialog () {
      FB.login(this.checkLoginState, { scope: 'email' })
    },
    checkLoginState: function (response) {
      if (response.status === 'connected') {        
        this.$emit('albumPage');
      } else if (response.status === 'not_authorized') {
        alert('Sorry, something wrong with app!');
      } else {
        alert('Please try again login');
      }
    },
  }
 };
</script>
<style scoped>
.login-block {
  height: 100vh;
}
.inner {
  padding: 2rem;
}
.inner.cover {
  border: 1px solid #f0f0f0;
  padding: 2.5rem;
}
.cover {
  padding: 0 1.5rem;
}
.cover .btn-lg {
  padding: .75rem 1.25rem;
  font-weight: bold;
}
</style>
