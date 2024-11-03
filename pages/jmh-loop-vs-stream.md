# Loops vs Streams Performance (ms/op)

<!-- Chart Container -->
<div class="chart-container">
  <div v-for="(size, index) in collectionSizes" :key="index" class="bar-group">
    <div class="bars">
      <!-- Loop Bar -->
      <div class="bar bar-loop" :style="{ height: `${loopTimes[index] * 0.5}px` }"> <!-- Scaled down by 0.5 -->
        <span class="bar-label">{{ loopTimes[index] }} </span>
      </div>
      <!-- Stream Bar -->
      <div class="bar bar-stream" :style="{ height: `${streamTimes[index] * 0.5}px` }"> <!-- Scaled down by 0.5 -->
        <span class="bar-label">{{ streamTimes[index] }} </span>
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
    <span>Loops</span>
  </div>
  <div class="legend-item">
    <div class="legend-color bar-stream"></div>
    <span>Streams</span>
  </div>
</div>

<script setup>
const collectionSizes = [ 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000];
const loopTimes = [       42,  86,  130, 182, 229, 282, 332, 370, 412, 479];
const streamTimes = [     46,  95,  140, 193, 254, 318, 357, 393, 441, 506];
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