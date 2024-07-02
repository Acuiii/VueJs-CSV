<template>
  <div class="container">
    <h1>Asset Management</h1>
    <table class="table">
      <thead>
        <tr>
          <th>Asset Name</th>
          <th>Department</th>
          <th>Printer</th>
          <th>HR</th>
          <th>Monitor</th>
          <th>IT</th>
          <th>Barcode Scanner</th>
          <th>Account</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in data" :key="index">
          <td>{{ item.assetName }}</td>
          <td>{{ item.department }}</td>
          <td>{{ item.printer }}</td>
          <td>{{ item.hr }}</td>
          <td>{{ item.monitor }}</td>
          <td>{{ item.it }}</td>
          <td>{{ item.barcodeScanner }}</td>
          <td>{{ item.account }}</td>
        </tr>
      </tbody>
    </table>
    <button @click="downloadCSV" class="btn">Download CSV</button>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true
    }
  },
  methods: {
    downloadCSV() {
      const header = Object.keys(this.data[0]).join(',') + '\n';
      const csv = this.data.map(item => Object.values(item).join(',')).join('\n');
      const blob = new Blob([header, csv], { type: 'text/csv' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'data.csv';
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    }
  }
};
</script>

<style scoped>
.container {
  width: 80%;
  margin: auto;
  padding: 20px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 20px;
}

.table th, .table td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: center;
}

.table th {
  background-color: #f2f2f2;
}

.btn {
  display: block;
  width: 100%;
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  text-align: center;
  border: none;
  cursor: pointer;
  font-size: 16px;
}

.btn:hover {
  background-color: #45a049;
}
</style>
