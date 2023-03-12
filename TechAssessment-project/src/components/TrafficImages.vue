<template>
    <div v-for="camera in cameras" class="col-lg-4">
        <div class="dropdown">
            <button class="btn dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                <Location :dateTime="dateTime" :locations="locations"/>
            </button>
            <ul class="dropdown-menu">
                <li class="text-center">
                    <img class="dropdown-item img-fluid" :src="camera.image">
                </li>
            </ul>
        </div>
    </div>

</template>

<script>
import Location from "./Location.vue"

export default {
    name: "TrafficImages",
    components:{
        Location
    },
    props:{
        'cameras': Array,
        'locations': Array,
        'dateTime': Object
    }
    ,
    data() {
        return {}
    },
    mounted(){
        
    }
}
</script>
