<template>
    <div>
        Location: {{ location_name }}
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Location',
    props: {
        'location': Array,
        'dateTime': Object
    },
    async mounted() {
        console.log("START weather forecast api")
        console.log(this.dateTime)

        const date = this.dateTime.date
        const hour = this.dateTime.hour
        const min = this.dateTime.min
        const sec = this.dateTime.sec

        this.api = `https://api.data.gov.sg/v1/environment/2-hour-weather-forecast?date_time=${date}T${hour}%3A${min}%3A${sec}`

        axios.get(this.api)
            .then(response => {
                console.log(response.data.area_metadata)
                this.areas = response.data.area_metadata
                location_name = getLocationName(this.areas)

            }).catch(error => {
                console.log("oh naur")
            })
        console.log("END weather forecast api")
    },
    methods:{
        getLocationName(areas){
            for(loc in locations){
                if(areas.label_location.latitude.tofixed(3) === loc.latitude.tofixed(3) && areas.label_location.longitude.tofixed(3) === loc.longitude.tofixed(3)){
                    this.location_names = areas.name
                }
            }

        }
    },
    data() {
        return {
            location_name: ""
        }
    }
}
</script>