<script setup>
definePageMeta({
  alias: "/home",
});
const bill = ref(0);
const people = ref(0);
const percentage = ref();

const tip = computed(function () {
  return (parseFloat(bill.value) * percentage.value) / parseFloat(people.value);
});
const totalAmount = computed(function () {
  return parseFloat(bill.value) / parseFloat(people.value) + tip.value;
});
</script>

<template>
  <div flex justify-center items-center h="100vh">
    <div class="card lg:card-side bg-base-100 shadow-xl">
      <div class="card-body">
        <div class="form-control w-full max-w-xs">
          <label class="label">
            <span class="label-text" text-base>Bill</span>
          </label>
          <input
            v-model="bill"
            type="text"
            placeholder="Type here"
            class="input input-bordered w-full max-w-xs"
            text-right
          />
        </div>
        <!-- Ende des Eingabefeldes -->

        <button class="btn btn-secondary" @click="percentage = 0.05">5%</button>
        <button class="btn btn-secondary" @click="percentage = 0.1">10%</button>
        <button class="btn btn-secondary" @click="percentage = 0.15">
          15%
        </button>
        <button class="btn btn-secondary" @click="percentage = 0.2">20%</button>
        <button class="btn btn-secondary" @click="percentage = 0.25">
          25%
        </button>
        <button class="btn btn-secondary" @click="percentage = 0.5">50%</button>
        <button class="btn btn-secondary">Custom</button>

        <div class="form-control w-full max-w-xs">
          <!--Anfang Number of People-->
          <label class="label">
            <span class="label-text" text-base>Number of people</span>
          </label>
          <input
            v-model="people"
            type="text"
            placeholder="Type here"
            class="input input-bordered w-full max-w-xs"
            text-right
          />
        </div>
        <!--Ende Number of People-->
      </div>
      <div class="card-body">
        <button class="btn">calculate tip</button>
        <div>
          <p>tip amount: {{ tip }}</p>
        </div>
        <div>
          <p>total: {{ totalAmount }}</p>
        </div>
        <button class="btn">Reset</button>
      </div>
    </div>
  </div>
</template>

<style>
/** {
  border: 1px solid red;
}*/
</style>
