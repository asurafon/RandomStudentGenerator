<template>
    <div>
        <br/><br/>
        <b-button variant="success" @click="generateRandomStudent">Generate</b-button>
    </div>
</template>

<script>
export default {
  name: 'randomStudent',
  props: {
    msg: String
  },
  methods:{
        generateRandomStudent(){
            var course = this.$route.params.course;
            console.log(course);
        },
        volver(){
            var course
            this.$router.push({name:'inicio'})
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
