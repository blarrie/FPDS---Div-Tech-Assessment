<script>
export default {

}
</script>

<template>
    <div class="form">

        <div>
            <p class="h3">Please select a date:</p>
            <input type="date" id="date">
        </div>

        <br>

        <div>
            <label for="time-input"></label>
            <p class="h3">Please select a time:</p>

            <label for="" class="time">HOUR</label>
            <select name="" id="">
                <option value="" v-for="hr in 24">
                    {{ hr }}
                </option>
            </select>

            <label for="minute" class="time">MINUTE</label>

            <select name="" id="minute">
                <option value="" v-for="(i, min) in 60"> 
                    {{ min }}
                </option>
            </select>

            <label for="second" class="time">SECOND</label>
            <select name="" id="second">
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
    font-family: Arial, Helvetica, sans-serif;
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


</style>