<script>
import axios from "axios"

export default {
    name: "TrafficImages",
    data() {
        return {
            list:[]
        }
    },

    async mounted() {
        console.log("---START traffic images API-----")
        // set api with date and time input
        // this.api = "https://api.data.gov.sg/v1/transport/traffic-images?date_time=" + {date} + "T" + {hr} + "%3A" + {min} + "%3A" + {sec}
        this.api = "https://api.data.gov.sg/v1/transport/traffic-images"

        // async api call
        axios.get(this.api)
            .then(response => {
                // get the long and lang 
                var allCameras = response.data.items[0].cameras
                this.list = allCameras

                // figure out how to get each camera in this array can i for loop this?
                console.log(this.list)
            })

        console.log("---END traffic images API-----")
    }
}
</script>

<template>
    <div>
        <img v-for="camera in list" :src="camera.image" class="img-fluid" alt="" >
    </div>
</template>