<template>
  <section>
      <h2>這是您的訂位紀錄:</h2>
      <div class="row" v-for="(booking,index) in bookings" :key="index">
        <div>{{booking.cabin}}</div>
      </div>
      <h3 class="row">Total:{{totalDisplay}}</h3>
  </section>
</template>

<script>
export default {
    props:{
        bookings:Array
    },
    computed:{
        totalDisplay(){
            let totalCost = 0;
            if(this.bookings && this.bookings.length>0){
                totalCost = this.bookings.map(x=>x.price).reduce((prev,obj)=>prev+obj);
            }
            return 'US$ ' + totalCost.toLocaleString('en-US');
        }
    }
}
</script>

<style>

</style>