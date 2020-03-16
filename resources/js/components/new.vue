<template>
    <div class="row">
   <div class="col-md-8">
            <div class="card card-default">
                <div class="card-header">Add Coin</div>

                <div class="card-body">

            <div class="form-group">
                <label  for="inputName">Name</label>
                <input  v-model="coins.stockName" type="text" class="form-control"  placeholder="">
            </div>
             <div class="form-group">
                <label  for="inputName">Year</label>
                <input v-model="coins.stockPrice"  type="text" class="form-control"  placeholder="">
            </div>
             <div class="form-group">
                <label  for="inputName">Price</label>
                <input v-model="coins.stockYear"  type="text" class="form-control"  placeholder="">
            </div>
<button type="submit" @click="addcoin" class="btn btn-primary">Submit</button>

                </div>
                </div>
                </div>
                </div>

</template>
<script>
import { Line } from 'vue-chartjs'

export default {
    extends : Line,

data() {
    return {
        coin:{},
        coins:{
            id :0 ,
            stockName : '',
            stockPrice : '',
            stockYear :'',



        }
    }
},
methods:{


    addcoin:function(){
       axios.post('/api/chart',this.coins)
       .then(response => {
           this.coins.id = response.data.id ;
            window.location.reload() ;
       })
       .catch(error => {
           console.log('error');
       })
    }
},


}
</script>
