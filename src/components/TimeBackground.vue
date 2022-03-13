<template>
    <!-- check morning -->
      <div class="morning" v-if="hours >= 5 && hours < 12">
        <ul>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
        </ul>
        <div class="sun-morning"></div>
      </div>
      <!-- check afternoon -->
    <div class="afternoon" v-else-if="hours >= 12 && hours < 18">
      <div class="sunx"></div>
      <div class="sun"></div>
    </div>

    <!-- check night -->
    <div class="night" v-else>
      <div class="moon"></div>
      <small class="spot1"></small>
      <small class="spot2"></small>
      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </div>
</template>

<script>

export default {
    name: 'TimeBackground',

    data(){
        return{
            hours: ''
        }
    }, 

    mounted(){
        //check hours
        this.hours = new Date().getHours()
        // console.log(this.hours)
    }
}


</script>