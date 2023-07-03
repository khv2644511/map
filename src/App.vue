<template>

  <v-app>
    <div style="padding: 20px">
    <v-row>  <h3>Kakao map demo</h3></v-row>
      <v-row>
        <v-btn
          @click="zoom(-1)"
          depressed
          outlined
          style="min-width: 30px;  height: 30px; padding: 3px;"
        >
        <v-icon dark small>
        mdi-plus
      </v-icon>
        </v-btn>
        <v-btn
          @click="zoom(1)"
          depressed
          outlined
          style="min-width: 30px;  height: 30px; padding: 3px;"
        >
        <v-icon dark small>
        mdi-minus
      </v-icon>
        </v-btn>
      </v-row>
     <v-row> <KakaoMap :options="mapOptions"/></v-row>
      <!-- <div class="kmap" ref="map"></div> -->
    </div>
    <v-main>
    </v-main>
  </v-app>
</template>

<script>
import KakaoMap from './components/map/kakaoMap.vue';

export default {
  name: 'App',

  components: {
    KakaoMap
},

  data: () => ({
    mapOptions: {
      center: {
        lat: 33.450701,
        lng: 126.570667
      },
      level: 8
    }
  }),
  mounted() {
    // let kakao = window.kakao
    // console.log(this.$refs.map)

    // let container = this.$refs.map; //지도를 담을 영역의 DOM 레퍼런스
    // let options = { //지도를 생성할 때 필요한 기본 옵션
    //   center: new kakao.maps.LatLng(33.450701, 126.570667), //지도의 중심좌표.
    //   level: 3 //지도의 레벨(확대, 축소 정도)
    // };
    // const mapInstance = new kakao.maps.Map(container, options); //지도 생성 및 객체 리턴
    // console.log(mapInstance)
  },
  methods: {
    zoom(delta) {
      // delta 1 or -1
      // console.log(delta)
      const level = Math.max(3, this.mapOptions.level + delta) // min level 3
      this.mapOptions.level = level
      console.log(this.mapOptions.level)
    } 
  }
};
</script>

<style>

</style>
