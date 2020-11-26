<template>
  <div id="body">
    <div id="header">Chart.js Random Demos</div>
    <div class="chart-container">
      <!-- Charts cannot be resized by the canvas element, 
    instead you create a parent element and size it from there,
    kind of like that charts container. -->
      <canvas id="myChart1"> <p>Your browser does not support charts</p></canvas>
    </div>
    <div class="chart-container">
      <canvas id="myChart2"> <p>Your browser does not support charts</p></canvas>
    </div>
    <div class="chart-container">
      <canvas id="myChart3"> <p>Your browser does not support charts</p></canvas>
    </div>
  </div>
</template>

<script>
import Chart from "chart.js";

export default {
  name: "ChartsDemo",
  props: {
    msg: String,
  },
  mounted() {
    var chartData = [12, 19, 3, 5, 2, 3];

    //Chart 1
    var ctx1 = document.getElementById("myChart1").getContext("2d");
    new Chart(ctx1, {
      type: "bar", //multiple types available; more in Chart.js documentation
      responsive: true,
      data: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [
          {
            label: "Label of chart",
            data: chartData,
            backgroundColor: ["rgba(255, 99, 132, 0.2)", "rgba(54, 162, 235, 0.2)", "rgba(255, 206, 86, 0.2)", "rgba(75, 192, 192, 0.2)", "rgba(153, 102, 255, 0.2)", "rgba(255, 159, 64, 0.2)"],
            borderColor: ["rgba(255, 99, 132, 1)", "rgba(54, 162, 235, 1)", "rgba(255, 206, 86, 1)", "rgba(75, 192, 192, 1)", "rgba(153, 102, 255, 1)", "rgba(255, 159, 64, 1)"],
            borderWidth: 3,
          },
        ],
      },
      options: {
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true, //axis value must bein at 0
              },
            },
          ],
        },
      },
    });
    // Chart 2
    var ctx2 = document.getElementById("myChart2").getContext("2d");
    new Chart(ctx2, {
      type: "line",
      responsive: true,
      data: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [
          {
            label: "Label of chart",
            data: chartData,
            backgroundColor: ["rgba(255, 99, 132, 0.2)", "rgba(54, 162, 235, 0.2)", "rgba(255, 206, 86, 0.2)", "rgba(75, 192, 192, 0.2)", "rgba(153, 102, 255, 0.2)", "rgba(255, 159, 64, 0.2)"],
            borderColor: ["rgba(255, 99, 132, 1)", "rgba(54, 162, 235, 1)", "rgba(255, 206, 86, 1)", "rgba(75, 192, 192, 1)", "rgba(153, 102, 255, 1)", "rgba(255, 159, 64, 1)"],
            borderWidth: 3,
          },
        ],
      },
      options: {
        elements: {
          line: {
            tension: 0, //To make grap line completely straight (no curves)
          },
        },
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
              },
            },
          ],
        },
      },
    });

    //Chart 3
    var ctx3 = document.getElementById("myChart3").getContext("2d");
    new Chart(ctx3, {
      type: "line",
      responsive: true,
      data: {
        labels: ["Jan", 'Feb', "Mar", 'April', 'May', 'June'],
        datasets: [
          {
            label: "Label of chart",
            data: [201, 339, 750, 400, 710, 525],
            backgroundColor: ["rgba(255, 255, 255, 0.2)", "rgba(255, 255, 255, 0.3)", "rgba(255, 255, 255, 0.3)", "rgba(255, 255, 255, 0.3)", "rgba(255, 255, 255, 0.3)", "rgba(255, 255, 255, 0.3)"],
            borderColor: ["rgba(99, 99, 255, 1)", "rgba(99, 99, 255, 1)", "rgba(99, 99, 255, 1)", "rgba(99, 99, 255, 1)", "rgba(99, 99, 255, 1)", "rgba(99, 99, 255, 1)"],
            borderWidth: 2,
          },
        ],
      },
      options: {
        scales: {
          xAxes: [{ position: "top" }],
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
                callback: function (value, index, values) { //to format final text at axis ticks (add currency symbol, units etc)
                  console.log(index, values);
                  return "₦" + value + 'K';
                },
              },
            },
          ],
        },
      },
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#body {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

#header {
  font-size: 27px;
  font-weight: 600;
  margin-bottom: 40px;
}

.chart-container {
  width: 100%;
  max-width: 500px;
  margin-bottom: 25px;
}
</style>
