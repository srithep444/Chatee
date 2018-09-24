<template>
  <div id="app" class="bg-component" >
    <button @click="sign()"> Facebook </button>
    <button @click="signOut()"> signout </button>
    <br>
    {{displayName}}
  </div>
</template>

<script>
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyBzDuIe1l8KLzZB3Uz9qZz5SkycRznrABo',
  authDomain: 'project-8399403142635038582.firebaseapp.com',
  databaseURL: 'https://project-8399403142635038582.firebaseio.com',
  projectId: 'project-8399403142635038582',
  storageBucket: 'project-8399403142635038582.appspot.com',
  messagingSenderId: '715949407192'
}
firebase.initializeApp(config)

var provider = new firebase.auth.FacebookAuthProvider()
provider.addScope('public_profile')
provider.setCustomParameters({
  'display': 'popup'
})
export default {
  name: 'App',

  data () {
    return {
      displayName: ''
    }
  },
  methods: {
    sign () {
      console.log('yes')
      var vm = this
      firebase.auth().signInWithPopup(provider).then(function (result) {
        var token = result.credential.accessToken
        var user = result.user
        console.log(token, user)
        console.log('displayName :: ', user.displayName)
        console.log('photoURL ::', user.photoURL)
        vm.displayName = user.displayName
        vm.photoURL = user.photoURL
      }).catch(function (error) {
        console.log(error)
      })
    },
    signOut () {
      var vm = this
      firebase.auth().signOut().then(function () {
        console.log('logOut')
        vm.displayName = ''
        vm.photoURL = ''
      }, function (error) {
        console.log(error)
      })
    }
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.bg-component {
  padding: 50px;
  background: url('../assets/img.jpg') 0 0 no-repeat;
  width: 100%;
}

</style>
