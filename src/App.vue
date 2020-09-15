<template>
  <div id="app">
    <!--
      Using the pie chart component and providing the pieData
    -->
    <PieChart :pieData="pieData" />
  </div>
</template>

<script>
  import PieChart from "./components/PieChart";

  export default {
    data: () => {
      return {
        /*
          Data for the pie chart, value is the percentage
        */
        pieData: [
          { color: "#0B6487", value: 30 },
          { color: "#9D1F37", value: 40 },
          { color: "#F6931C", value: 30 }
        ]
      };
    },
    components: {
      PieChart
    }
  };
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-size: 1rem;
  font-family: Tahoma;
  background-color: #333;
  color: #fefefe;
}

#app {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 100vh;
  width: 100%;
  padding: 20px;
}
</style>

