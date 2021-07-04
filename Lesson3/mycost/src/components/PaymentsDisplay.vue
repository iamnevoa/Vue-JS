<template>
  <div class="list">
    <table>
      <thead>
        <tr class="table-data">
          <th>#</th>
          <th>Date</th>
          <th>Category</th>
          <th>Value</th>
        </tr>
      </thead>
      <tbody>
        <tr class="item" v-for="(item, idx) in items" :key="idx">
          <td class="table-index">{{ idx + 1 }}</td>
          <td class="table-date">{{ item.date }}</td>
          <td class="table-category">{{ item.category }}</td>
          <td class="table-value">{{ item.value }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "PaymentsDisplay",
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
<style >
.table-data {
  text-align: left;
}
.table-index {
  width: 50px;
}
.table-date {
  width: 150px;
}
.table-category {
  width: 150px;
}
.table-value {
  width: 100px;
}
td {
  height: 30px;
}
</style>

