<script>
export default {
  name: 'GasPrice',
  data() {
    return {
      average: 0,
      safeLow: 0,
      fast: 0,
      fastest: 0,
    }
  },
  methods: {
    loadData() {
      /*$.get('/api/data', function (response) {
        // TODO: save data
      }.bind(this));*/
      console.log("loadData");
      this.average += 0.1;
      this.safeLow += 0.1;
      this.fast += 0.1;
      this.fastest += 0.1;
    }
  },
  created() {
    this.interval = setInterval(() => this.loadData(), 1000);
  }
}
</script>

<template>
  <p>Average : {{average}}</p>
  <p>Safe Low : {{safeLow}}</p>
  <p>Fast : {{fast}}</p>
  <p>Average : {{fastest}}</p>
</template>

<style scoped>
</style>