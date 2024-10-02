
<template>
  <div>
    <h2>Sales Data by Month</h2>
    <canvas id="salesChart"></canvas>

    <h2>Sales Data by Day</h2>
    <canvas id="dailySalesChart"></canvas>

    <h2>Sales Data by Week</h2>
    <canvas id="weeklySalesChart"></canvas>
  </div>
</template>

<script>
import axios from 'axios';
import {
  Chart,
  BarController,
  BarElement,
  CategoryScale,
  LinearScale,
  Title,
  Tooltip,
  Legend,
} from 'chart.js'; // Import required components

// Register the components
Chart.register(BarController, BarElement, CategoryScale, LinearScale, Title, Tooltip, Legend);

export default {
  data() {
    return {
      salesData: [],
      dailySalesData: [],
      weeklySalesData: [],
      months: [],
      totals: [],
      dailyTotals: [],
      dailyDates: [],
      weeklyTotals: [],
      weeklyDates: [],
      chart: null,          // Monthly chart instance
      dailyChart: null,     // Daily chart instance
      weeklyChart: null,    // Weekly chart instance
    };
  },
  methods: {
    // Fetch monthly sales data
    async fetchSalesData() {
      try {
        const response = await axios.get('/api/dashboard/sales'); // Fetch API data
        this.salesData = response.data;

        this.salesData.forEach(item => {
          this.months.push(this.getMonthName(item.date)); // Convert month number to name
          this.totals.push(item.total_sales); // Push total sales
        });

        this.renderSalesChart();  // After fetching data, render the chart
      } catch (error) {
        console.error("Error fetching sales data:", error);
      }
    },

    // Fetch daily sales data
    async fetchDailySalesData() {
      try {
        const response = await axios.get('/api/dashboard/daily-sales');
        this.dailySalesData = response.data;

        this.dailySalesData.forEach(item => {
          this.dailyDates.push(`${item.year}-${item.month}-${item.day}`); // Format as YYYY-MM-DD
          this.dailyTotals.push(item.total_sales);
        });

        this.renderDailySalesChart();
      } catch (error) {
        console.error("Error fetching daily sales data:", error);
      }
    },

    // Fetch weekly sales data
    async fetchWeeklySalesData() {
      try {
        const response = await axios.get('/api/dashboard/weekly-sales');
        this.weeklySalesData = response.data;

        this.weeklySalesData.forEach(item => {
          this.weeklyDates.push(`Week ${item.week}, ${item.year}`); // Format as Week X, Year
          this.weeklyTotals.push(item.total_sales);
        });

        this.renderWeeklySalesChart();
      } catch (error) {
        console.error("Error fetching weekly sales data:", error);
      }
    },

    getMonthName(month) {
      const monthNames = ["January", "February", "March", "April", "May", "June", 
                          "July", "August", "September", "October", "November", "December"];
      return monthNames[month - 1];
    },

    // Render monthly sales chart
    renderSalesChart() {
      if (this.chart) {
        this.chart.destroy(); // Destroy existing chart if present
      }

      const ctx = document.getElementById('salesChart').getContext('2d');
      this.chart = new Chart(ctx, {
        type: 'bar',
        data: {
          labels: this.months,
          datasets: [{
            label: 'Total Sales',
            data: this.totals,
            backgroundColor: 'rgba(75, 192, 192, 0.2)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1,
          }],
        },
        options: {
          scales: {
            y: {
              beginAtZero: true,
            },
          },
        },
      });
    },

    // Render daily sales chart
    renderDailySalesChart() {
      if (this.dailyChart) {
        this.dailyChart.destroy(); // Destroy existing chart if present
      }

      const ctx = document.getElementById('dailySalesChart').getContext('2d');
      this.dailyChart = new Chart(ctx, {
        type: 'bar',
        data: {
          labels: this.dailyDates,
          datasets: [{
            label: 'Daily Sales',
            data: this.dailyTotals,
            backgroundColor: 'rgba(153, 102, 255, 0.2)',
            borderColor: 'rgba(153, 102, 255, 1)',
            borderWidth: 1,
          }],
        },
        options: {
          scales: {
            y: {
              beginAtZero: true,
            },
          },
        },
      });
    },

    // Render weekly sales chart
    renderWeeklySalesChart() {
      if (this.weeklyChart) {
        this.weeklyChart.destroy(); // Destroy existing chart if present
      }

      const ctx = document.getElementById('weeklySalesChart').getContext('2d');
      this.weeklyChart = new Chart(ctx, {
        type: 'bar',
        data: {
          labels: this.weeklyDates,
          datasets: [{
            label: 'Weekly Sales',
            data: this.weeklyTotals,
            backgroundColor: 'rgba(255, 159, 64, 0.2)',
            borderColor: 'rgba(255, 159, 64, 1)',
            borderWidth: 1,
          }],
        },
        options: {
          scales: {
            y: {
              beginAtZero: true,
            },
          },
        },
      });
    }
  },
  mounted() {
    this.fetchSalesData();        // Fetch monthly sales data
    this.fetchDailySalesData();    // Fetch daily sales data
    this.fetchWeeklySalesData();   // Fetch weekly sales datad
  },
};
</script>


<style scoped>
canvas {
  width: 90% !important;
  height: 500px !important;
}
</style>


