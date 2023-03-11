<script>
export default {
    name: "Form",
    data() {
        return {
            date: "",
            hour: "",
            min: "",
            sec: "",
        };
    },
    methods: {
        postData(e) {
            console.log(this.date);
            console.log(this.hour);
            console.log(this.min);
            console.log(this.sec);

            e.preventDefault();
        },
    },
};
</script>

<template>
    <div class="form">
        <form @submit="postData" method="post">
            <div>
                <p class="h3">Please select a date:</p>
                <input type="date" id="date" name="date" v-model="date" />
            </div>

            <br/>

            <div >
            
                <p class="h3">Please select a time:</p>
                    <label for="" class="time">HOUR</label>
                    <select class="form-select" name="hour" id="hour" v-model="hour">
                        <option value="" v-for="hr in 24">
                            {{ hr }}
                        </option>
                    </select>

                    <label for="minute" class="time">MINUTE</label>
                    <select class="form-select" name="min" id="minute" v-model="min">
                        <option :value="{ min }" v-for="(i, min) in 60">
                            {{ min }}
                        </option>
                    </select>

                    <label for="second" class="time">SECOND</label>
                    <select class="form-select" name="sec" id="second" v-model="sec">
                        <option value="" v-for="(i, sec) in 60">
                            {{ sec }}
                        </option>
                    </select>
            </div>

            <button class="btn btn-primary m-3" type="submit">Submit</button>
        </form>
    </div>
</template>

<style scoped>
.form {
    margin: auto;
    /* border: 1px solid white; */
    text-align: center;
    font-family: Arial, Helvetica, sans-serif;
}

.time {
    padding-left: 5px;
    padding-right: 5px;
    font-size: large;
}

#date {
    font-size: large;
    border-radius: 9px;
}
</style>
