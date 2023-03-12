<script setup>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import axios from "axios"
import Form from './components/Form.vue'
import TrafficImages from './components/TrafficImages.vue'
import Header from './components/Header.vue'

</script>

<template>
  <div class="main"> 
    <Header />
    <div class="container text-center">
      <div class="row my-2">
        <Form @add-date-time="fetchImages" />
      </div>

      <div class="row">
        <TrafficImages :cameras="cameras" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  methods: {
    async fetchImages(dateTime) {
      console.log("START traffic images api")
      const date = dateTime.date
      const hour = dateTime.hour
      const min = dateTime.min
      const sec = dateTime.sec

      this.api = `https://api.data.gov.sg/v1/transport/traffic-images?date_time=${date}T${hour}%3A${min}%3A${sec}`

      axios.get(this.api)
        .then(response => {
          console.log(response.data)
          this.cameras = response.data.items[0].cameras
          for (this.cam in this.cameras) {
            // console.log(this.cameras[this.cam].location.longitude)
            this.location = this.cameras[this.cam].location
            this.locations.push(this.location)
          }
        })
      console.log("END traffic images api")

    },
    async fetchLocation() {

    }
  },
  data() {
    return {
      cameras: [],
      locations: []
    }
  }

}
</script>
