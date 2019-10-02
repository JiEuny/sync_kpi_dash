<template>
  <div class="group">
    <el-main>
        <!-- <div v-for="history in histories" v-bind:key="history.rn">
            <h3>{{history.rn}}</h3>
        </div>
        group
        <button v-on:click="momentTest">moment test</button> -->
        <canvas ref="myChart" id="myChart" class="chart-container"/>
        <br/>
        <br/>
        <div>
            <b-table striped hover :items="items"></b-table>
        </div>
    </el-main>
      
  </div>
</template>

<script>
import VueMomentJS from 'vue-momentjs'
import moment from 'moment'
import Vue from 'vue'
import chart from 'chart.js'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue)
Vue.use(VueMomentJS, moment)

var secondListA = [];
var secondListB = [];

export default {
    name: "Group",
    methods: {
        momentTest: function() {
            var test = this.$moment(this.histories[0].startTime);
            var end = this.$moment(this.histories[0].endTime);
            
            console.log(this.$moment(test).format('YYYY-MM-DD-hh-mm-ss'));
            console.log(this.$moment(end).format('YYYY-MM-DD-hh-mm-ss'));
            console.log(this.$moment(test).day());
            console.log(end.diff(test, 'seconds'));
            // 0: 일, 1: 월, 2: 화. 3: 수, 4: 목, 5: 금, 6: 토
        }
    },
    mounted() {

        for (var i = 0; i < this.histories.length; i++) {
            if(this.histories[i].lbl == "A") {
                secondListA.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
            } else {
                secondListB.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
            }
        }
        
        console.log('a;'+secondListA);
        console.log('b;'+secondListB);

        const average = array => (array && array.length) ? (array.reduce((sum, item) => sum + item, 0) / array.length) : undefined;
        this.items.push({time:"Total", Group_A: average(secondListA), Group_B: average(secondListB), "B-A":average(secondListB)-average(secondListA)});

        var tempChart = new chart(this.$refs.myChart.getContext('2d'), {
            type: 'bar',
            data: {
                labels: ['A', 'B'],
            // labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
            datasets: [{
                label: 'Group',
                data: [average(secondListA), average(secondListB)],
                backgroundColor: [
                    'rgba(255, 99, 132, 0.2)',
                    'rgba(54, 162, 235, 0.2)',
                    'rgba(255, 206, 86, 0.2)',
                    'rgba(75, 192, 192, 0.2)',
                    'rgba(153, 102, 255, 0.2)',
                    'rgba(255, 159, 64, 0.2)'
                ],
                borderColor: [
                    'rgba(255, 99, 132, 1)',
                    'rgba(54, 162, 235, 1)',
                    'rgba(255, 206, 86, 1)',
                    'rgba(75, 192, 192, 1)',
                    'rgba(153, 102, 255, 1)',
                    'rgba(255, 159, 64, 1)'
                    ],
                    borderWidth: 1
                }] 
            },
            options: {
                tooltips: {
                    xlabel: 'group',
                    ylabel: 'time'
                },
                scales: {
                    yAxes: [{
                        ticks: {
                            beginAtZero: true
                        }
                    }]
                }
            }
        });
    },
  data() {
    return {
        items: [],
      histories: [
        {
          rn: "flx-3K593C",
          ty: 28,
          pi: "SkmnDBfeHX",
          ri: "SymEIuUHrQ",
          ct: "20180806T051036",
          et: "20210806T051036",
          lt: "20180806T051036",
          st: 8929,
          cnd: "http://developers.iotocean.org/schema/parkingHistory.xsd",
          type: "ParkingHistory",
          startTime: "20190821T145822",
          endTime: "20190821T145841",
          lbl: [
              "A"
          ],
          beaconData: {
              major: 18,
              minor: 19
          },
          refParkingLot: "wdc_base/sync_parking/parkingLot_1",
          parkingLocation: {
              type: "Point",
              coordinates: [
                  37.4037059,
                  127.1594274
              ]
          },
          appOS: "iOS",
          appVersion: "1.0.0"
        },
        {
          rn: "flx-3K593D",
          ty: 28,
          pi: "SkmnDBfeHX",
          ri: "SymEIuUHrQ",
          ct: "20180806T051036",
          et: "20210806T051036",
          lt: "20180806T051036",
          st: 8929,
          cnd: "http://developers.iotocean.org/schema/parkingHistory.xsd",
          type: "ParkingHistory",
          startTime: "20190821T145822",
          endTime: "20190821T145859",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          },
          refParkingLot: "wdc_base/sync_parking/parkingLot_1",
          parkingLocation: {
              type: "Point",
              coordinates: [
                  37.4037059,
                  127.1594274
              ]
          },
          appOS: "iOS",
          appVersion: "1.0.0"
        },
        {
          rn: "flx-3K593D",
          ty: 28,
          pi: "SkmnDBfeHX",
          ri: "SymEIuUHrQ",
          ct: "20180806T051036",
          et: "20210806T051036",
          lt: "20180806T051036",
          st: 8929,
          cnd: "http://developers.iotocean.org/schema/parkingHistory.xsd",
          type: "ParkingHistory",
          startTime: "20190821T145822",
          endTime: "20190821T145850",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          },
          refParkingLot: "wdc_base/sync_parking/parkingLot_1",
          parkingLocation: {
              type: "Point",
              coordinates: [
                  37.4037059,
                  127.1594274
              ]
          },
          appOS: "iOS",
          appVersion: "1.0.0"
        }
      ]
    }
  }
}
</script>

<style scoped>
.chart-container {
    height: 50vh;
    width: 50vw;
}
</style>