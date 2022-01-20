<template>
    <div class="mapPane">
        <!--マップ-->
        <l-map
            :zoom="zoom"
            :center="center"
        >
            <!--レイヤーコントロール-->
            <l-control-layers
                position="topright"
            ></l-control-layers>
            <!--レイヤ設定-->
            <l-tile-layer
                v-for="tileProvider in tileProviders"
                :key="tileProvider.name"
                :name="tileProvider.name"
                :visible="tileProvider.visible"
                :url="tileProvider.url"
                :attribution="tileProvider.attribution"
                layer-type="base"
            ></l-tile-layer>
            <!--マーカー-->
            <l-marker
                :lat-lng="marker"
            ></l-marker>
        </l-map>
    </div>
</template>

<script lang="ts">
import {
    LMap,
    LTileLayer,
    LControlLayers,
    LMarker
} from '@vue-leaflet/vue-leaflet';

export default {
    name: 'MapPane',
    components: {
        LMap,
        LTileLayer,
        LControlLayers,
        LMarker
    },
    data() {
        return {
            center: [35.681, 139.763],
            zoom: 14,
            marker: [35.681, 139.763],
            tileProviders: [
                {
                    name: 'MIERUNE Streets',
                    visible: true,
                    url: 'https://api.maptiler.com/maps/jp-mierune-streets/256/{z}/{x}/{y}.png?key=[APIキー]',
                    attribution: '<a href="https://maptiler.jp/" target="_blank">&copy; MIERUNE</a> <a href="https://www.maptiler.com/copyright/" target="_blank">&copy; MapTiler</a> <a href="https://www.openstreetmap.org/copyright" target="_blank">&copy; OpenStreetMap contributors</a>'
                },
                {
                    name: 'MIERUNE Gray',
                    visible: false,
                    url: 'https://api.maptiler.com/maps/jp-mierune-gray/256/{z}/{x}/{y}.png?key=[APIキー]',
                    attribution: '<a href="https://maptiler.jp/" target="_blank">&copy; MIERUNE</a> <a href="https://www.maptiler.com/copyright/" target="_blank">&copy; MapTiler</a> <a href="https://www.openstreetmap.org/copyright" target="_blank">&copy; OpenStreetMap contributors</a>'
                }
            ]
        }
    }
}
</script>

<style scoped>
.mapPane {
    height: 800px;
    margin: 0;
    text-align: left;
}
</style>
