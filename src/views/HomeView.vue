<template>
  <div class="home">
    <add-places @add-entry="addTableEntry" />
    <item :tableData="tableData" />
  </div>
</template>

<script>
import { ref } from 'vue';
import AddPlaces from '@/components/forms/AddPlaces.vue';
import Item from '@/components/Places/Item.vue';

export default {
  name: 'HomeView',
  components: {
    AddPlaces,
    Item
  },
  setup() {
    const tableData = ref([]);

    const addTableEntry = (input) => {
      tableData.value.push({ input: input, checked: false });
    };

    return { tableData, addTableEntry };
  },
};
</script>

<style>
.home {
  /* 您的 CSS 樣式 */
}
</style>