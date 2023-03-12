<template>
    <div class="form col-md-6">
        <form @submit="onSubmit" action="">

            <div>
                <p class="h3">Please select a date:</p>
                <input type="date" id="date" name="date" v-model="date" />
            </div>

            <div>
                <p class="h3">Please select a time:</p>

                <label for="hour" class="time">HOUR</label>
                <select class="form-select" name="hour" id="hour" v-model="hour">
                    <option :value="hour.toString()" v-for="hour in 24">
                        {{ hour }}
                    </option>
                </select>

                <label for="minute" class="time">MINUTE</label>
                <select class="form-select" name="min" id="minute" v-model="min">
                    <option :value="min.toString()" v-for="(i, min) in 60">
                        {{ min }}
                    </option>
                </select>

                <label for="second" class="time">SECOND</label>
                <select class="form-select" name="sec" id="second" v-model="sec">
                    <option :value="sec.toString()" v-for="(i, sec) in 60">
                        {{ sec }}
                    </option>
                </select>
            </div>
            <button class="btn btn-primary m-3" type="submit" >Submit</button>
        </form>
    </div>
</template>

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
        convertDate(year,mth,day){
            if(mth < 10){
                mth = '0' + mth
            }
            if(day < 10){
                day = '0' + day
            }

            return `${year}${mth}${day}`
        },
        onSubmit(e) {
            e.preventDefault()
            var date = new Date();
            var currDate = this.convertDate(date.getFullYear(),date.getMonth() + 1,date.getDate())
            var selectedDate = this.date.replaceAll('-','')


            if(selectedDate > currDate){
                alert("Please a pick a valid date")
                return
            }

            if(!this.date){
                alert("Please select a date")
                return
            }

            if(!this.hour){
                alert("Please select an hour")
                return
            }

            if(!this.min){
                alert("Please select a minute")
                return
            }

            if(!this.sec){
                alert("Please select a second")
                return
            }
            if(this.hour.length < 2){
                this.hour = '0' + this.hour
            }
            if(this.min.length < 2){
                this.min = '0' + this.min
            }
            if(this.sec.length < 2){
                this.sec = '0' + this.sec
            }

            const dateTime = {
                date: this.date,
                hour: this.hour,
                min: this.min,
                sec: this.sec
            }

            // console.log(dateTime)
            this.$emit('add-date-time', dateTime)

            this.date = ""
            this.hour = ""
            this.min = ""
            this.sec = ""
        }
    },
};
</script>

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
    margin-top: 5px;
}

#date {
    font-size: large;
    border-radius: 9px;
}
</style>
