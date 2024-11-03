# Lambda vs Method Reference (ms/op)


<!-- Chart Container -->
<div class="chart-container">
  <div v-for="(size, index) in collectionSizes" :key="index" class="bar-group">
    <div class="bars">
      <!-- Loop Bar -->
      <div class="bar bar-loop" :style="{ height: `${methodReferenceTimes[index] * 5}px` }"> <!-- Scaled down by 0.5 -->
        <span class="bar-label">{{ methodReferenceTimes[index] }} </span>
      </div>
      <!-- Stream Bar -->
      <div class="bar bar-stream" :style="{ height: `${lambdaExpressionTimes[index] * 5}px` }"> <!-- Scaled down by 0.5 -->
        <span class="bar-label">{{ lambdaExpressionTimes[index] }} </span>
      </div>
    </div>
    <!-- Collection Size Label -->
    <div class="size-label">{{ size }}k</div>
  </div>
</div>

<!-- Legend -->
<div class="legend">
  <div class="legend-item">
    <div class="legend-color bar-loop"></div>
    <span>Method reference</span>
  </div>
  <div class="legend-item">
    <div class="legend-color bar-stream"></div>
    <span>Lambda expression</span>
  </div>
</div>

<script setup>
const collectionSizes = [ 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000];
const methodReferenceTimes = [2.67,  5.85,  12.8, 17.7, 21.4, 27.0, 32.6, 39.2, 42.8, 51.4];
const lambdaExpressionTimes = [3.01,  5.93,  12.7, 18.0, 22.0, 29.1, 32.5, 39.9, 42.7, 52.9];
</script>


<style>
.legend {
  display: flex;
  gap: 15px;
  justify-content: center;
  margin-top: 15px;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
}

.legend-color {
  width: 15px;
  height: 15px;
}

.bar-loop, .legend-color.bar-loop {
  background-color: #6baed6;
}

.bar-stream, .legend-color.bar-stream {
  background-color: #fd8d3c;
}

/* Existing styles for the chart */
.chart-container {
  display: flex;
  gap: 20px;
  align-items: flex-end;
  justify-content: center;
  height: 300px;
}

.bar-group {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.bars {
  display: flex;
  gap: 5px;
  align-items: flex-end;
}

.bar {
  width: 20px;
  position: relative;
}

.bar-label {
  position: absolute;
  bottom: -15px;
  font-size: 10px;
  text-align: center;
  width: 100%;
}

.size-label {
  margin-top: 20px;
  font-size: 12px;
  font-weight: bold;
  text-align: center;
}
</style>
