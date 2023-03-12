<script setup>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import axios from "axios"
import Form from './components/Form.vue'
import TrafficImages from './components/TrafficImages.vue'
import Header from './components/Header.vue'

</script>

<template>
  <Header />
  <div class="container text-center">
    <div class="row my-2">
      <Form @add-date-time="fetchImages" />
    </div>

    <div class="row">
      <TrafficImages :cameras="cameras" />
    </div>

  </div>
</template>

<script>
export default {
  name: "App",

  methods: {
    async fetchImages(dateTime) {

      const date = dateTime.date
      const hour = dateTime.hour
      const min = dateTime.min
      const sec = dateTime.sec

      this.api = `https://api.data.gov.sg/v1/transport/traffic-images?date_time=${date}T${hour}%3A${min}%3A${sec}`

      axios.get(this.api)
        .then(response => {
          console.log(response.data)
          this.cameras = response.data.items[0].cameras
        })

    }
  },
  data() {
    return {
      cameras: []
    }
  }

}
</script>


<style scoped>
@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
