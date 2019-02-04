<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/student.png">
    <h1>Random Student Generator </h1>
    <br/>
    <router-link :to="{name: 'randomStudentV', params: {course: 'M'}}">Monday</router-link>
    <br/>
    <br/>
    <router-link :to="{name: 'randomStudentV', params: {course: 'W'}}">Wednesday</router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import RandomStudent from '@/components/RandomStudent.vue'

export default {
  name: 'home',
  components: {
    RandomStudent
  }
}
</script>
