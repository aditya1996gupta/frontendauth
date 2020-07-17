<template>
    <div>
        <h2>Login</h2>
        <form v-on:submit="login">
         <input type="text" name="email" placeholder='email'/><br>
         <input type="password" name="password" placeholder='password'/><br>
            <input type="submit" value="Login" />
        </form>
    </div>
</template>

<script>
import router from '../router'
import axios from 'axios'
export default {
  name: 'Login',
  methods: {
    login: (e) => {
      e.preventDefault()
      let email = 'user@email.com'
      let password = 'password'
      let login = () => {
        let data = {
          email: email,
          password: password
        }
        axios.post('/api/login', data)
          .then((response) => {
            console.log('Logged in')
            router.push('/dashboard')
          })
          .catch((errors) => {
            console.log('Cannot log in')
          })
      }
      login()
    }
  }
}
</script>

<style>
.input {
padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}
</style>
