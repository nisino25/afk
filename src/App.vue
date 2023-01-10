<template>
  <div class="clock">
    <div class="test"></div>
    <div class="main">
      <div class="first-circle circle"></div>
      <div class="second-circle circle"></div>
      <div class="third-circle circle"></div>
      <div class="forth-circle circle"></div>

      <div class="number-wrapper">
        <template v-for="i in hoursList" :key="i">
          <!-- <div style="position:absolute; top:50%;left:50%; "> -->
          <div style="position:absolute; top:50%;left:50%;" :style="getHoursStyle(i)" >
            <!-- {{getHoursStyle(i)}} -->
            {{i }}
          </div>
        </template>
      </div>
    </div>
    <div class="base"></div>
  </div>

  {{ time }}
</template>

<script>

  export default {
    name: 'App',
    components: {
      
    },
    data(){
      return{
        hours: 0,
        minutes: 0,
        seconds: 0,

        showingTime: undefined,

        hoursList: [1,2,3,4,5,6,7,8,9,10,11,12]
      }
    },
    methods:{
      sleep(ms) {
        return new Promise((resolve) => {
          setTimeout(resolve, ms);
        });
      },
      updatedTime(){
        const d = new Date();

        this.hours = d.getHours();
        this.minutes = d.getMinutes();
        this.seconds = d.getSeconds();

        if(this.hours < 10){
          this.hours = `0${this.hours}`
        }
        if(this.minutes < 10){
          this.minutes = `0${this.minutes}`
        }
        if(this.seconds < 10){
          this.seconds = `0${this.seconds}`
        }
        //   this.sleep(500)
        //   count++
  
        // }
      },

      getHoursStyle(i){
        let top
        let left

        if(i == 12) top = -460
        if(i == 1 || i == 11) top = -400
        if(i == 2 || i == 10) top = -250
        if(i == 3 || i == 9) top = -50
        if(i == 4 || i == 8) top = 150
        if(i == 5 || i == 7) top = 305
        if(i == 6) top = 360

        
        
        
        
        if(i == 9) left = -1000
        if(i == 8) left = -850
        if(i == 10) left = -445
        if(i == 7) left = -500
        if(i == 11) left = -270
        if(i == 12 || i ==6) left = -50
        if(i == 1 || i == 5) left = 400
        if(i == 2 || i == 4) left = 750
        if(i == 3) left= 900
        

        // // top = top * 100
        // // return top

        return `transform: translate(${left}%,${top}%);`

        // return `top:${top}%; left: ${left}%`

        // return `transform: rotate(calc(30deg * ${i}))`
      }
    },
    mounted(){
      console.clear()
      setInterval(() => this.updatedTime(), 500)

      // setTimeout(this.updatedTime(), 500);
    },
    computed:{
      time(){
        return `${this.hours}:${this.minutes}:${this.seconds}`
      }
    },

  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    /* color: #2c3e50; */
    margin-top: 60px;

    
  }

  html{
    background-color:  #121212;
    color: darkgrey;
  }

  .clock{
    position: absolute;
    aspect-ratio: 1/1;
    
    width: 600px;
    /* height: 600px; */
    max-width: 90vw;

    /* background-color: white; */

    top:50%;
    left:50%;
    transform: translate(-50%,-50%);
  }

  .main{
    position: absolute;
    border-radius: 50%;
    background-color:  #121212;

    aspect-ratio: 1/1;
    width: 100%;

    -moz-box-shadow: -1px -1px 76px -19px rgba(150, 143, 150, 0.46);
    -webkit-box-shadow: -1px -1px 76px -19px rgba(150, 143, 150, 0.46);
    -ms-box-shadow: -1px -1px 76px -19px rgba(150, 143, 150, 0.46);
    box-shadow: -1px -1px 76px -19px rgba(150, 143, 150, 0.46);
  }

  .circle{
    position: absolute;
    border-radius: 50%;
    border: 2px solid white;
    /* background-color:  white; */

    aspect-ratio: 1/1;
    

    top:50%;
    left:50%;
    transform: translate(-50%,-50%);
  }

  .first-circle{
    width: 70%;
    /* width: 90%;
    background-image: linear-gradient(150deg, white 50%, transparent 50%), linear-gradient(0deg, transparent 50%, white 50%);  */
    /* background-image:  linear-gradient(45deg, transparent 50%, white 50%); */
  }

  .second-circle{
    width: 60%;
    /* width: 50%; */
  }

  .test{
/* 
    position: absolute;

    width: 300px;
     height: 300px;
     background: orange;
     border-radius: 50%;
     background-image: linear-gradient(0deg, white 50%, transparent 50%), linear-gradient(45deg, transparent 50%, white 50%); */


    /* position: absolute;
    width: 100%;
    height: 30%;
    opacity: 0.5;
    top:50%;
    background: red;
    z-index: 100; */

    /* transform: translateX(-50%); */
  }

  .third-circle{
    width: 45%;
  }

  .forth-circle{
    width: 8%;
  }  

  .number-wrapper{
    font-size: 300%;
    font-weight: bold;
    text-align: center;
    /* inset: 20px; */
  }

  .base{

  }


</style>
