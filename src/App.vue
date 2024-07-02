<template>
  <div id="app">
    <DataDisplay :data="assetData" />
  </div>
</template>

<script>
import DataDisplay from './components/DataDisplay.vue';

export default {
  name: 'App',
  components: {
    DataDisplay
  },
  data() {
    return {
      assetData: [
        {
          assetName: 'Printer',
          department: 'IT',
          printer: 'Yes',
          hr: 'No',
          monitor: 'No',
          it: 'Yes',
          barcodeScanner: 'No',
          account: 'No'
        },
        {
          assetName: 'Monitor',
          department: 'HR',
          printer: 'No',
          hr: 'Yes',
          monitor: 'Yes',
          it: 'No',
          barcodeScanner: 'No',
          account: 'No'
        },
        {
          assetName: 'Barcode Scanner',
          department: 'ACCOUNT',
          printer: 'No',
          hr: 'No',
          monitor: 'No',
          it: 'No',
          barcodeScanner: 'Yes',
          account: 'Yes'
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
