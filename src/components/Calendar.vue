<template>
       <div class="datas">
          <h1>Vue Calendar App</h1>
            <div class="label">
                <h2 class="currentmonthlabel">{{currentMonthName}} </h2>
                <h2 class="currentyearlabel">{{currentYear}} </h2>
            </div>
          
            <section class="days">
                <p v-for="day in days" :key="day">{{day}}</p>
            </section>
            
            <section class="numbers">
                <p v-for="num in startDay()" :key="num"></p>
                <p v-for="num in daysInMonth()" :key="num" > <span :class="currentDateClass(num)">{{num}}</span> </p>
            </section>


            <section class="buttons">
                <button class="prev"  @click="Prev">Prev</button>
                <button class="next"  @click="Next">Next</button>

            </section>

        </div>
</template>

<script>
export default {

    data(){
        return{
            // currentDate: new Date().getUTCDate(),
            currentMonth: new Date().getMonth(),
            currentYear: new Date().getFullYear(),
            days: ['Sun','Mon','Tue','Wed','Thu','Fri','Sat']
        }
    },
    methods:{
        daysInMonth(){
        return new Date(this.currentYear, this.currentMonth+1, 0).getDate();
        },

        startDay(){
            return new Date(this.currentYear,this.currentMonth, 1, 1).getDay();
        },
        
        Next(){
            if(this.currentMonth == 11){
               this.currentMonth = 0;
               this.currentYear++;
            }else{
              this.currentMonth++; 
            }

             
            
        },
        Prev(){
         if(this.currentMonth == 0){
             this.currentMonth = 11;
               this.currentYear--;
         }else{
            this.currentMonth--;
        }
      },

      currentDateClass(num){
               const calendarFullDate =  new Date(this.currentYear,this.currentMonth,num).toDateString();
               const currentFullDate =  new Date().toDateString();
               return calendarFullDate === currentFullDate ? 'badge' : ' ';
      }
    },

    computed:{
        currentMonthName(){
            return  new Date(this.currentYear,this.currentMonth).toLocaleString('default',{month:'long'});
        },

        getcurrentDay(){
        return new Date().toDateString();
        }
    }
    
}
</script>

<style scoped>

   .datas{
    background-color: rgba(112, 207, 99, 0.39);
    padding: 40px;
  }
  

  .datas h1{
    text-align: center;
    padding: 10px;
  }

  section {
    display: flex;
    margin: 0px 10px 0px 10px;
    text-align: center;
    flex-wrap: wrap;
  }

  .days p{
      padding:25px;
      width: 15px;
    
  }

  .numbers p {
      flex-basis: 14%;
  }

  .label{
      display: flex;
      flex-direction: row;
      flex-basis: 100%;
      
  }

  .currentmonthlabel{
      padding-left: 30px;
      font-weight: bolder;
      justify-content: left;
      text-align: left;
      flex-basis: 50%;
  
  }

    .currentyearlabel{
       padding-right: 35px;
      font-weight: bolder;
     justify-content: right;
      text-align: right;
       flex-basis: 50%;
  }

  .buttons{
      display: flex;
      flex-direction: row;
      flex-basis: 100%;
      justify-content:space-between;
      padding-top: 20px;
  }

  .buttons .prev{
      margin-left:20px;
      font-weight: bolder;
      padding: 10px;
      border: none;
      color: black;
      font-weight: bolder;
     
  
  }

    .buttons .next{
      margin-right:20px;
      font-weight: bolder;
       padding: 10px;
      border: none;
      color: black;
      font-weight: bolder;
  
  }

  .badge{
      background-color: #fff;
      padding: 5px;
  }



  @media (max-width:999px) {
       .days p{
         /* display: none;   */
         padding: 17px;
       }
  }

   @media (max-width:439px) {
       .days p{
         padding: 13px;
       }
  }

   @media (max-width:339px) {
       .days p{
         padding: 9px;
         /* display: none; */
       }
  }
</style>