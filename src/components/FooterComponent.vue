<template>
    <footer>
      {{ years }} - powered by: Rafael Coding
      <a href="https://github.com/rafael-coding/weather-app" target="_blank" rel="noopener noreferrer">
        <img src="../assets/git.png" alt="">
      </a>
    </footer>
</template>

<script>

export default {
    name: 'FooterComponent',

    data(){
        return{
            years: ''
        }
    }, 

    mounted(){
        //check years
        this.years = new Date().getFullYear()
        // console.log(this.years)
    }
}

</script>

<style>
 @import '/src/assets/app';

</style>