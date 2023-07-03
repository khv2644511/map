<template>
    <div class="kmap" ref="map"></div>
</template>

<script>
    export default {
    props: ['options'],
    data() {
        return {
                mapInstance: null
            }
        },
        mounted() {
            let kakao = window.kakao
            // console.log(this.$refs.map)

            let container = this.$refs.map //지도를 담을 영역의 DOM 레퍼런스
            // let options = { //지도를 생성할 때 필요한 기본 옵션
            //   center: new kakao.maps.LatLng(33.450701, 126.570667), //지도의 중심좌표.
            //   level: 3 //지도의 레벨(확대, 축소 정도)
            // };
            const { center, level } = this.options
            this.mapInstance = new kakao.maps.Map(container, {
                center: new kakao.maps.LatLng(center.lat, center.lng),
                level: level,
            }) //지도 생성 및 객체 리턴
            // console.log(this.mapInstance)
    },
    watch: {
        'options.level'(cur, prev) {
                console.log(`[LEVEL CANGED] ${prev}=> ${cur}`)
                this.mapInstance.setLevel(cur)
            }
        }
    }
</script>

<style>
.kmap {
  width: 100%;
  height: 600px;
}
</style>