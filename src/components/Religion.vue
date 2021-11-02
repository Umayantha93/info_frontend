<template>
  <div class="container" id="chart">
    <pie-chart :data="chartData" :options="chartOptions"></pie-chart>
  </div>
</template>

<script>
import axios from "axios";
import PieChart from "../PieChart";
export default {
  name: "Religion",
  components: {
    PieChart
  },

    methods:{
        getData(){
          axios.get('http://127.0.0.1:8000/api/user-religion')
          .then((response)=>{ this.data = response.data
              var items = this.data //gets you array
              for (var i = 0; i < items .length; i++) { 
                this.chartData['labels'].push(items[i].religion);
                this.count.push(items[i].user_count);
                // var id = items[i].Id;
              // console.log("Name:"+name + " Id:"+id+"\n");
        }
        // this.chartData['labels'].push(this.religions)
        // console.log(this.religions);
        // console.log(this.count)
        console.log(this.chartData);
          })
        },
              forceRerender(){
        this.componentkey += 1
      }
      },

      created() {
        this.getData()
        this.forceRerender()
      }, 


  data() {
    return {

      religions:[],
      count:[],
      componentkey: 0,
      chartOptions: {
      hoverBorderWidth: 20
      },

      chartData: {
        hoverBackgroundColor: "red",
        hoverBorderWidth: 10,
        labels:[],
        datasets: [
          {
            label: "Data One",
            backgroundColor: ["#41B883", "#E46651", "#00D8FF"],
            data: [1, 10, 5]
          }
        ]
      }
    };
  },

  }
</script>

<style scope>
#chart {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container{
  width: 20%;
  height: 20%;
}
</style>