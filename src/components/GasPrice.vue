<script>

export default {
  name: 'GasPrice',
  data() {
    return {
      average: '-',
      safeLow: '-',
      fast: '-',
      fastest: '-',
    }
  },
  methods: {
    async loadData() {
      fetch('https://data-api.defipulse.com/api/v1/egs/api/ethgasAPI.json').then(
        (response) => {
          if (response.status !== 200) {
            console.log('API returned status code : ' + response.status);
            return;
          }

          response.json().then((data) => {
            this.average = data.average / 10;
            this.safeLow = data.safeLow / 10;
            this.fast = data.fast / 10;
            this.fastest = data.fastest / 10;
          });
        }
      ).catch((err) => {
        console.warn('Fetch Error :', err);
      });
    }
  },
  created() {
    this.loadData()
    this.interval = setInterval(() => this.loadData(), 5000);
  }
}
</script>

<template>
  <p>Average : {{average}} gwei</p>
  <p>Safe Low : {{safeLow}} gwei</p>
  <p>Fast : {{fast}} gwei</p>
  <p>Average : {{fastest}} gwei</p>
</template>

<style scoped>
</style>