<script setup>
// TODO 4: Declare the activeFilter prop and the filter and sort events.
const props = defineProps({
  activeFilter: String,
});

const emit = defineEmits(["filter", "sort"]);
// Write onSortChange(event).
function onSortChange(event) {
  emit("sort", event.target.value);
}
</script>

<template>
  <!-- TODO 4: The filter buttons and sort menu. See README.md for the markup. -->
  <div class="controls">
    <div class="filters" role="group" aria-label="Filter animals">
      <button
        type="button"
        :class="{ active: props.activeFilter === 'all' }"
        @click="emit('filter', 'all')"
      >
        All
      </button>
      <button
        type="button"
        :class="{ active: props.activeFilter === 'available' }"
        @click="emit('filter', 'available')"
      >
        Available
      </button>
      <button
        type="button"
        :class="{ active: props.activeFilter === 'adopted' }"
        @click="emit('filter', 'adopted')"
      >
        Adopted
      </button>
    </div>

    <label for="sort-animals">Sort by:</label>
    <select id="sort-animals">
      <option value="default">Original order</option>
      <option value="name">Name</option>
      <option value="age">Age</option>
    </select>
  </div>
</template>
