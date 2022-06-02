<template>
<div class = "about">
    <div id="chart">
    <BarChart />
    <LineChart />
    </div>
<iframe 
    width="100%" 
    height="900px" 
    src="https://embed.windy.com/embed2.html?lat=16.172&lon=106.392&detailLat=21.031&detailLon=105.852&width=650&height=450&zoom=5&level=surface&overlay=wind&product=ecmwf&menu=&message=&marker=&calendar=now&pressure=&type=map&location=coordinates&detail=&metricWind=default&metricTemp=default&radarRange=-1" frameborder="0">
    </iframe>
</div>
</template>
<script>
import BarChart from '../components/BarChart.vue'
import LineChart from '../components/LineChart.vue'
export default {
    name: 'App',
    components: {  BarChart, LineChart }
}
</script>
<style >
*{
    margin: 0;
    padding: 0;
}
.about{
    background-image: linear-gradient(to bottom, rgba(102, 126, 234, 1), rgb(88, 195, 245));
    width: 100%;
    height: auto;
    display: flex;
    justify-content: center;
    align-items: center;
}
#chart{
    display: block;
}
</style>