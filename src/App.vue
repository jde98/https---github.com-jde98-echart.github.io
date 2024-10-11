<script setup>
import { onMounted, ref } from 'vue';
import * as echarts from 'echarts';

const chart1 = ref(null);
const chart2 = ref(null);
const chart3 = ref(null);


const initChart = () => {

  const barChart = echarts.init(chart1.value);
  const lineChart = echarts.init(chart2.value);
  const pieChart = echarts.init(chart3.value);

  // 차트 옵션 설정
  const barOption = {
    title: {
      text: 'ECharts 기본 예제',
    },
    tooltip: {},
    xAxis: {
      data: ['A', 'B', 'C', 'D', 'E'],
    },
    yAxis: {},
    series: [
      {
        name: '판매량',
        type: 'bar',
        data: [5, 20, 36, 10, 10],
      },
    ],
  };

  const lineOption = {
    xAxis: {
      type: 'category',
      data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    yAxis: {
      type: 'value'
    },
    series: [
      {
        data: [150, 230, 224, 218, 135, 147, 260],
        type: 'line'
      }
    ]
  };

  const pieOption = {
    title: {
      text: 'Referer of a Website',
      subtext: 'Fake Data',
      left: 'center'
    },
    tooltip: {
      trigger: 'item'
    },
    legend: {
      orient: 'vertical',
      left: 'left'
    },
    series: [
      {
        name: 'Access From',
        type: 'pie',
        radius: '50%',
        data: [
          { value: 1048, name: 'Search Engine' },
          { value: 735, name: 'Direct' },
          { value: 580, name: 'Email' },
          { value: 484, name: 'Union Ads' },
          { value: 300, name: 'Video Ads' }
        ],
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          }
        }
      }
    ]
  };

  // 옵션 적용
  barChart.setOption(barOption);
  lineChart.setOption(lineOption);
  pieChart.setOption(pieOption);
};  

// 컴포넌트가 마운트될 때 차트 초기화
onMounted(() => {
  initChart();
});

</script>

<template>
  <div ref="chart1" style="width: 100%; height: 400px;"></div>
  <div ref="chart2" style="width: 100%; height: 400px;"></div>
  <div ref="chart3" style="width: 100%; height: 400px;"></div>
</template>

<style scoped>  
</style>
