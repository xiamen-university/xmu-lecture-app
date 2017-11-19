<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="queryLectureEvents">Get Lecture Events</button>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'hello', // component name
  data () {
    return {
      msg: 'Welcome to XMU Lecture Web App'
    }
  },
  methods: {
    queryLectureEvents: (e) => {
      e.preventDefault()
      axios.get('https://lecture.xmu.edu.cn/events', {
        headers: {
          'Access-Control-Allow-Origin': '*'
        },
        crossdomain: true
      })
        .then(response => {
          console.log('response: ', response)
        })
        .catch(error => {
          console.error('error: ', error)
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #35495E;
}
</style>
