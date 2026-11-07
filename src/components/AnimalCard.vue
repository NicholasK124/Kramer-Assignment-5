<script setup>
import dayjs from "dayjs";
// TODO 2: Declare the animal prop with defineProps().
defineProps({
  animal: Object,
});

function arrivalText(intakeDate) {
  const arrived = dayjs(intakeDate);

  return `Arrived ${arrived.format("MMM DD, YYYY")} (${dayjs().diff(arrived, "day")} days ago)`;
}

// TODO 3: Declare the toggle event with defineEmits().
/**
 * ---------------------------Required Comment------------------------------
 * In this component, we define a prop called `animal` using `defineProps()`,
 * which allows us to pass an animal object from the parent component.
 * We also define a function called `arrivalText()` that takes an intake date
 * and returns a formatted string indicating when the animal arrived and how many days ago that was.
 */
const emit = defineEmits(["toggle"]);
</script>

<template>
  <!-- TODO 2: Build one animal's card. See README.md for the markup. -->

  <article class="animal-card">
    <h3>{{ animal.name }}</h3>
    <p>{{ animal.species }}, {{ animal.age }} years old</p>
    <p>{{ arrivalText(animal.intakeDate) }}</p>
    <p>{{ animal.adopted ? "Adopted" : "Available" }}</p>
    <button type="button" @click="emit('toggle')">
      {{ animal.adopted ? "Return" : "Adopt" }}
    </button>
  </article>
</template>
