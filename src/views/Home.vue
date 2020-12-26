<template>
  <div class="home">
    <input type="text" v-model="text">
    <button @click="send">送信</button>
    <p>{{getData}}</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      text: "",
      getData: ""
    }
  },
  methods: {
    send() {
      axios
        .post('http://localhost:8001/api/', {
          text: this.text
        })
        .then((response) => {
          this.getData = response.data.data
          console.log(response.data.data)
        })
    }
  },
}
</script>
