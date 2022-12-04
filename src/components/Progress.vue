<template>
  <div class="progress" v-if="(progressBar > 0)">
    <div class="progress-bar bg-info" role="progressbar" :style="'width:' + progressBar + '%'" aria-valuenow="50"
      aria-valuemin="0" aria-valuemax="100">
      {{ productCount }} / 10
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main';

export default {
  data() {
    return {
      progressBar: 0,
      productCount: 0,
    }
  },
  created() {
    eventBus.$on("progressUpdate", (item) => {
      this.productCount = item;
      this.progressBar = item * 10;
    })
  }
}
</script>