<script>
</script>

<template>
    <div class="form">

        <div>
            <h2>Please select a date:</h2>
            <input type="date" id="date">
        </div>

        <br>

        <div id="timeInput">
            <h2>Please select a time:</h2>

            <label for="" class="time">HOUR</label>
            <select name="" id="">
                <option value="" v-for="hr in 24">
                    {{ hr }}
                </option>
            </select>

            <label for="" class="time">MINUTE</label>
            <select name="" id="">
                <option value="" v-for="(i, min) in 60"> 
                    {{ min }}
                </option>
            </select>

            <label for="" class="time">SECOND</label>
            <select name="" id="">
                <option value="" v-for="(i, sec) in 60"> 
                    {{ sec }}
                </option>
            </select>

        </div>


    </div>
</template>

<style scoped>

.form{
    margin: auto;
    /* border: 1px solid white; */
    text-align: center;
}

.time{
    padding-left: 5px;
    padding-right: 5px;
    font-size: large;
}

#date{
    font-size: large;
    border-radius: 9px;
}

#timeInput{
    flex: auto;
}

</style>