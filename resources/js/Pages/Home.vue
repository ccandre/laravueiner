<script setup>
import Button from "primevue/button"
import Chart from 'primevue/chart'
import { ref, onMounted } from "vue";



onMounted(() => {
    chartData.value = setChartData();
    chartOptions.value = setChartOptions();
});

const chartData = ref();
const chartOptions = ref();

const setChartData = () => {
    const documentStyle = getComputedStyle(document.body);

    return {
        labels: ['Aloha', 'Banana', 'Cola'],
        datasets: [
            {
                data: [540, 325, 702],
                backgroundColor: [documentStyle.getPropertyValue('--p-cyan-500'), documentStyle.getPropertyValue('--p-orange-500'), documentStyle.getPropertyValue('--p-gray-500')],
                hoverBackgroundColor: [documentStyle.getPropertyValue('--p-cyan-400'), documentStyle.getPropertyValue('--p-orange-400'), documentStyle.getPropertyValue('--p-gray-400')]
            }
        ]
    };
};

const setChartOptions = () => {
    const documentStyle = getComputedStyle(document.documentElement);
    const textColor = documentStyle.getPropertyValue('--p-text-color');

    return {
        plugins: {
            legend: {
                labels: {
                    usePointStyle: true,
                    color: textColor
                }
            }
        }
    };
};
</script>

<template>
    <div class="flex h-screen bg-green-100">
        <!-- Sidebar -->
        <aside class="w-16 bg-white shadow-lg p-3">
            <ul class="space-y-4">
                <li class="hover:bg-gray-100 p-2 rounded-md transition-colors cursor-pointer text-gray-700">Icon 1</li>
                <li class="hover:bg-gray-100 p-2 rounded-md transition-colors cursor-pointer text-gray-700">Icon 2</li>
            </ul>
        </aside>
    
    
    

    <!-- Main Content -->



        <!-- Main Content -->
        <main class="flex-1 p-6 space-y-6">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-white p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow">
                    <h2 class="text-xl font-semibold text-green-800 mb-2">Box 1</h2>
                    <div class="card flex justify-center">
                        <Chart type="pie" :data="chartData" :options="chartOptions" class="w-full md:w-[30rem]" />
                    </div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow">
                    <h2 class="text-xl font-semibold text-gray-800 mb-2">Box 2</h2>
                    <div class="card flex justify-center">
                        <Button label="Verify" />
                    </div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow">
                    <h2 class="text-xl font-semibold text-gray-800 mb-2">Box 3</h2>
                    <p class="text-gray-600">Content for box 3</p>
                </div>
            </div>
        </main>
    </div>
</template>
