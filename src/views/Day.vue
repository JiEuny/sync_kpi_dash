<template>
  <div class="day">
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

var secondListAMON = [];
var secondListATUE = [];
var secondListAWED = [];
var secondListATHU = [];
var secondListAFRI = [];
var secondListBMON = [];
var secondListBTUE = [];
var secondListBWED = [];
var secondListBTHU = [];
var secondListBFRI = [];

export default {
    name: "Day",
    mounted() {

        for (var i = 0; i < this.histories.length; i++) {
            if(this.histories[i].lbl == "A") {
                switch(this.$moment(this.histories[i].startTime).day()) {
                    case 1:
                        secondListAMON.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 2:
                        secondListATUE.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 3:
                        secondListAWED.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 4:
                        secondListATHU.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 5:
                        secondListAFRI.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                }
            } else {
                switch(this.$moment(this.histories[i].startTime).day()) {
                    case 1:
                        secondListBMON.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 2:
                        secondListBTUE.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 3:
                        secondListBWED.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 4:
                        secondListBTHU.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 5:
                        secondListBFRI.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                }

            }
        }

        const average = array => (array && array.length) ? (array.reduce((sum, item) => sum + item, 0) / array.length) : undefined;
        this.items.push({day:"Monday", Group_A: average(secondListAMON), Group_B: average(secondListBMON), "B-A":average(secondListBMON)-average(secondListAMON)});
        this.items.push({day:"Tuesday", Group_A: average(secondListATUE), Group_B: average(secondListBTUE), "B-A":average(secondListBTUE)-average(secondListATUE)});
        this.items.push({day:"Wednesday", Group_A: average(secondListAWED), Group_B: average(secondListBWED), "B-A":average(secondListBWED)-average(secondListAWED)});
        this.items.push({day:"Thursday", Group_A: average(secondListATHU), Group_B: average(secondListBTHU), "B-A":average(secondListBTHU)-average(secondListATHU)});
        this.items.push({day:"Friday", Group_A: average(secondListAFRI), Group_B: average(secondListBFRI), "B-A":average(secondListBFRI)-average(secondListAFRI)});

        var tempChart = new chart(this.$refs.myChart.getContext('2d'), {
            type: 'line',
            data: {
                labels: ['MON', 'TUE', 'WED', 'THU', 'FRI'],
                datasets: [{
                    label: 'GroupA',
                    data: [average(secondListAMON), average(secondListATUE), average(secondListAWED), average(secondListATHU), average(secondListAFRI)],
                    backgroundColor: 'rgba(255,99,132,1)',
                    borderColor: 'rgba(255,99,132,1)',
                    borderWidth: 1,
                    fill: false
                },
                {
                    label: 'GroupB',
                    data: [average(secondListBMON), average(secondListBTUE), average(secondListBWED), average(secondListBTHU), average(secondListBFRI)],
                    backgroundColor: 'rgba(102, 179, 255,1)',
                    borderColor: 'rgba(102, 179, 255,1)',
                    borderWidth: 1,
                    fill: false
                }] 
            },
            options: {
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
          startTime: "20190820T145822",
          endTime: "20190820T145850",
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
          startTime: "20190820T145822",
          endTime: "20190820T145850",
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
          startTime: "20190819T145822",
          endTime: "20190819T145830",
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
          startTime: "20190819T145822",
          endTime: "20190819T145850",
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
          startTime: "20190822T145822",
          endTime: "20190822T145845",
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
          startTime: "20190822T145822",
          endTime: "20190822T145840",
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
          startTime: "20190823T145820",
          endTime: "20190823T145845",
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
          startTime: "20190823T145820",
          endTime: "20190823T145840",
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