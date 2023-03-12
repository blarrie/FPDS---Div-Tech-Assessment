<template>
    <div v-for="camera in cameras" class="col-lg-4">
        <div class="dropdown">
            <button class="btn dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                <!-- Location: {{ camera.location }} -->
                Location
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

export default {
    name: "TrafficImages",
    props:['cameras']
    ,
    data() {
        return {}
    },
    methods:{

    }
}
</script>
