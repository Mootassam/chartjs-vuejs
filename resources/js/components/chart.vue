<script>
import { Line } from 'vue-chartjs';

export default {
   extends: Line,
   mounted() {

         let Year = new Array();
         let  Name = new Array();
         let Price = new Array();
         axios.get('/api/chart')
         .then((response) => {
            let data = response.data;
            if(data) {
               data.forEach(element => {
               Year.push(element.stockYear);
                Name.push(element.stockName);
              Price.push(element.stockPrice);
               });
               this.renderChart({
                labels: Year,
               datasets: [{
                  label: 'Chart of amount of people this year',
                  backgroundColor: '#FC2525',
                  data: Price
            }]
         }, {responsive: true, maintainAspectRatio: false})
       }
       else {
          console.log('No data');
       }
      });
   }
}
</script>
