<template>
  <div id="app">
    <el-main>
      <!-- <Group v-bind:histories="histories" /> -->
      home
    </el-main>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Group from './Group'
import exios from 'axios';

export default {
  name: 'home',
  components: {
    Group
  },
  data() {
    return {
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
          endTime: "20190821T145841",
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

