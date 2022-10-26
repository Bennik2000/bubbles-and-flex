<script>

import * as echarts from 'echarts';

// initialize the echarts instance
export default {
    mounted() {
        let categories = [{ name: 'Bubble' }, { name: 'Person' }];
        let nodes = [];
        let links = [];


        for (let i = 0; i < 200; i++) {
            nodes.push(
                {
                    id: i.toString(),
                    name: "Node " + i,
                    symbolSize: Math.floor(Math.random() * 20),
                    x: Math.random() * 100,
                    y: Math.random() * 100,
                    value: Math.floor(Math.random() * 100),
                    category: Math.floor(Math.random() * categories.length),
                    label: { show: true }
                }
            );
        }

        for (let i = 0; i < 150; i++) {
            links.push(
                {
                    source: Math.floor(Math.random() * 100),
                    target: Math.floor(Math.random() * 100)
                }
            );
        }


        var myChart = echarts.init(this.$el);
        myChart.showLoading();

        nodes.forEach(function (node) {
            node.label = {
                show: node.symbolSize > 30
            };
        });

        let option = {
            title: {
                text: 'Enterprise Bubbles',
                subtext: 'Default layout',
                top: 'bottom',
                left: 'right'
            },
            tooltip: {},
            legend: [
                {
                    data: categories.map(function (a) {
                        return a.name;
                    })
                }
            ],
            animationDuration: 1500,
            animationEasingUpdate: 'quinticInOut',
            series: [
                {
                    name: 'Les Miserables',
                    type: 'graph',
                    layout: 'none',
                    data: nodes,
                    links: links,
                    categories: categories,
                    roam: true,
                    label: {
                        position: 'right',
                        formatter: '{b}'
                    },
                    lineStyle: {
                        color: 'source',
                        curveness: 0.3
                    },
                    emphasis: {
                        focus: 'adjacency',
                        lineStyle: {
                            width: 10
                        }
                    }
                }
            ]
        };

        myChart.hideLoading();
        myChart.setOption(option);
    }
}
</script>

<template>
    <div id="chart" class="h-100"></div>
</template>

<style scoped>
.h-100 {
  flex-shrink: 0;
  flex: auto;
  width: 100%;
}
</style>
