<template>
  <div class="time">
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

var secondListA07 = [];
var secondListA08 = [];
var secondListA09 = [];
var secondListA10 = [];
var secondListA11 = [];
var secondListA12 = [];
var secondListA13 = [];
var secondListA14 = [];
var secondListA15 = [];
var secondListB07 = [];
var secondListB08 = [];
var secondListB09 = [];
var secondListB10 = [];
var secondListB11 = [];
var secondListB12 = [];
var secondListB13 = [];
var secondListB14 = [];
var secondListB15 = [];
export default {
    name: "Time",
    mounted() {
        for (var i = 0; i < this.histories.length; i++) {
            if(this.histories[i].lbl == "A") {
                switch(this.$moment(this.histories[i].startTime).hour()) {
                    case 7:
                        secondListA07.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 8:
                        secondListA08.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 9:
                        secondListA09.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 10:
                        secondListA10.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 11:
                        secondListA11.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 12:
                        secondListA12.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 13:
                        secondListA13.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 14:
                        secondListA14.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 15:
                        secondListA15.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                }
            } else {
                switch(this.$moment(this.histories[i].startTime).hour()) {
                    case 7:
                        secondListB07.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 8:
                        secondListB08.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 9:
                        secondListB09.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 10:
                        secondListB10.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 11:
                        secondListB11.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 12:
                        secondListB12.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 13:
                        secondListB13.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 14:
                        secondListB14.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                    case 15:
                        secondListB15.push(this.$moment(this.histories[i].endTime).diff(this.$moment(this.histories[i].startTime), 'seconds'));
                        break;
                }

            }
        }

        const average = array => (array && array.length) ? (array.reduce((sum, item) => sum + item, 0) / array.length) : undefined;
        this.items.push({time:"07:00", Group_A: average(secondListA07), Group_B: average(secondListB07), "B-A":average(secondListB07)-average(secondListA07)});
        this.items.push({time:"08:00", Group_A: average(secondListA08), Group_B: average(secondListB08), "B-A":average(secondListB08)-average(secondListA08)});
        this.items.push({time:"09:00", Group_A: average(secondListA09), Group_B: average(secondListB09), "B-A":average(secondListB09)-average(secondListA09)});
        this.items.push({time:"10:00", Group_A: average(secondListA10), Group_B: average(secondListB10), "B-A":average(secondListB10)-average(secondListA10)});
        this.items.push({time:"11:00", Group_A: average(secondListA11), Group_B: average(secondListB11), "B-A":average(secondListB11)-average(secondListA11)});
        this.items.push({time:"12:00", Group_A: average(secondListA12), Group_B: average(secondListB12), "B-A":average(secondListB12)-average(secondListA12)});
        this.items.push({time:"13:00", Group_A: average(secondListA13), Group_B: average(secondListB13), "B-A":average(secondListB13)-average(secondListA13)});
        this.items.push({time:"14:00", Group_A: average(secondListA14), Group_B: average(secondListB14), "B-A":average(secondListB14)-average(secondListA14)});
        this.items.push({time:"15:00", Group_A: average(secondListA15), Group_B: average(secondListB15), "B-A":average(secondListB15)-average(secondListA15)});

        var tempChart = new chart(this.$refs.myChart.getContext('2d'), {
            type: 'line',
            data: {
                labels: ['07', '08', '09', '10', '11', '12', '13', '14', '15'],
                datasets: [{
                    label: 'GroupA',
                    data: [average(secondListA07), average(secondListA08), average(secondListA09), average(secondListA10), average(secondListA11), average(secondListA12), average(secondListA13), average(secondListA14), average(secondListA15)],
                    backgroundColor: 'rgba(255,99,132,1)',
                    borderColor: 'rgba(255,99,132,1)',
                    borderWidth: 1,
                    fill: false
                },
                {
                    label: 'GroupB',
                    data: [average(secondListB07), average(secondListB08), average(secondListB09), average(secondListB10), average(secondListB11), average(secondListB12), average(secondListB13), average(secondListB14), average(secondListB15)],
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
          }
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
          startTime: "20190821T115822",
          endTime: "20190821T115850",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T075822",
          endTime: "20190821T075840",
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
          startTime: "20190821T075822",
          endTime: "20190821T075845",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T085800",
          endTime: "20190821T085825",
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
          startTime: "20190821T085800",
          endTime: "20190821T085828",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T095800",
          endTime: "20190821T095828",
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
          startTime: "20190821T095800",
          endTime: "20190821T095828",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T105800",
          endTime: "20190821T105825",
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
          startTime: "20190821T105800",
          endTime: "20190821T105819",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
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
          startTime: "20190821T115800",
          endTime: "20190821T115819",
          lbl: [
              "A"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T125800",
          endTime: "20190821T125825",
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
          startTime: "20190821T125800",
          endTime: "20190821T125830",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T135801",
          endTime: "20190821T135825",
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
          startTime: "20190821T135800",
          endTime: "20190821T135830",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
        },
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
          startTime: "20190821T155801",
          endTime: "20190821T155830",
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
          startTime: "20190821T155800",
          endTime: "20190821T155825",
          lbl: [
              "B"
          ],
          beaconData: {
              major: 18,
              minor: 19
          }
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