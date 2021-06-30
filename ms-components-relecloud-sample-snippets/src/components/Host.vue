<template>
  <section>
      <div class="nav-bar"></div>
      <h1>Relecloud Galaxy Tours</h1>
      <div>
          <h2>{{cruise.name}}</h2>
          <div>{{cruise.description}}</div>
          <hr>
          <div class="row">
              <div><!--TODO add booking-form -->
                <bookin-form @bookingCreated="addBooking" :cabins="cruise.cabins"></bookin-form>
              </div>
              <div><!--TODO add booking-list -->
                <booking-list :bookings="bookings"></booking-list>
              </div>
          </div>
      </div>
  </section>
</template>

<script>
import BookingList from './BookingList.vue'
//TODO: Register next component
import BookinForm from './BookingForm.vue'
export default {
    data(){
        return{
            cruise:{
                name:'月球之旅',
                description:'超奢華、超精彩、超刺激',
                cabins:[
                    {name:'Coach',price:125000},
                    {name:'Business',price:275000},
                    {name:'First',price:430000},
                ]
            },
            bookings:[
                {name:'Sample',price:0}
            ]
        }
    },
    //TODO : Add Components
    components:{
        BookingList,
        //TODO: Add next component
        BookinForm
    },
    //TODO : Add methods
    methods:{
        addBooking(cabinIndex){
            const cabin = this.cruise.cabins[cabinIndex];
            const booking = {
                cabin:cabin.name,
                price:cabin.price
            };
            this.bookings.push(booking);
        }
    }
}
</script>

<style>
    body{
        background-color: #f2f2f2;
        margin: 0,5%;
        font-family: tahoma;
    }
    .row{
        display: grid;
        grid-template-columns: 1fr 1fr;
        vertical-align: middle;
        margin: 2em;
    }
    .button{
        background-color: #39495c;
        border-radius: 5px;
        color: white;
        text-align: center;
    }
    .nav-bar{
        background: linear-gradient(-50deg, #010801,#0d0d60);
        height: 60px;
        margin-bottom: 25px;
    }
</style>