<template>
    <div>
        <br/><br/>
        <b-button variant="success" @click="generateRandomStudent">Generate</b-button>
        <b-button variant="danger" @click="reset">Reset</b-button>
        <br/><br/><br/>
        <div>
            <p>
                And the Oscar goes to...
            </p>        
            <IOdometer class="iOdometer" :value="num" :theme="car"/>
        </div>   
        <div v-if="showWinner" class="winner">
            <b-alert variant="success" show>
                {{name}}
            </b-alert>            
        </div>    
    </div>
</template>

<script>
import IOdometer from 'vue-odometer';
import 'odometer/themes/odometer-theme-default.css';
import 'odometer/themes/odometer-theme-car.css';

import 'odometer/themes/odometer-theme-car.css';
import mondayList from '@/assets/data/mondayList.json';
import wednesdayList from '@/assets/data/wednesdayList.json';

export default {
    name: 'randomStudent',
    props: {
        msg: String
    },
    components: {
      IOdometer
    },
    data() {
        return {
            num: 0,
            listOfClass: null,
            showWinner: false,
            name: null
        };
    },  
    methods:{
        generateRandomStudent(){
            this.showWinner = false;
            this.name = null;
            var course = this.$route.params.course;
            var studentsId = new Array();
            this.listOfClass.forEach(member => {
                if(member.coupleId == null)
                    studentsId.push(member.id);
            });
            var randomNumber = Math.floor(Math.random() * studentsId.length);
            var constant = 95;
            
            //console.log(randomNumber);
            this.num = randomNumber;
            
            this.listOfClass.forEach(member => {
                if(member.id == studentsId[this.num])
                    this.name = member.name;
            });

            var self = this;
            var time = constant*randomNumber;
            
            setTimeout(function(){
                self.showWinner = true;
            },time);

            
        },
        reset(){
            this.num = 0;
            this.showWinner = false;
            this.name = null;
        },

    },
    created(){
        var module = this.$route.params.course;
        this.listOfClass = module == 'M' ? mondayList : wednesdayList;
        //console.log(this.listOfClass);
        /*const that = this;
        //that.num = 99;
        setTimeout(function() {
            that.num = 99;
        }, 1000);*/
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .iOdometer {
        font-size: 60px;
        margin: 0;
    }

    p{
        font-size: 70px;
    }

    button {
        margin: 0px 10px;
    }
    
    .winner{
        font-size: 75px;
        margin-top: 60px;
    }
</style>
