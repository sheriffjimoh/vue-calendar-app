<template>
      <div  id="app">
         <Calendar />
       
      </div>
</template>

<script>

import Calendar from './components/Calendar.vue';
export default {

  components: {
    Calendar
  
  }
  
}
</script>

<style scoped>

*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

 
  #app{

    padding-top: 5rem;
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }


</style>
