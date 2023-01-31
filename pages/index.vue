<script setup>
definePageMeta({
  alias: "/home",
});
const bill = ref(0);
const people = ref(0);
const percentage = ref();
const showCustomPercentage = ref(false);
const customPercentage = ref(1);
const currencyDollar = 1.08;

const tip = computed(function () {
  if (showCustomPercentage.value)
    return (
      (parseFloat(bill.value) * customPercentage.value) /
      100 /
      parseFloat(people.value)
    );
  return (parseFloat(bill.value) * percentage.value) / parseFloat(people.value);
});
const totalAmount = computed(function () {
  return parseFloat(bill.value) / parseFloat(people.value) + tip.value;
});

function reset() {
  people.value = 0;
  percentage.value = 0;
  bill.value = 0;
}
function switchCurrency() {}
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
        <!-- Ende des Eingabefeldes -->
        <div>
          <button
            class="btn btn-outline btn-success"
            @click="percentage = 0.05"
          >
            5%
          </button>
          <button class="btn btn-outline btn-success" @click="percentage = 0.1">
            10%
          </button>
          <button
            class="btn btn-outline btn-success"
            @click="percentage = 0.15"
          >
            15%
          </button>
        </div>
        <div>
          <button
            class="btn btn-outline btn-success"
            @click="percentage = 0.25"
          >
            25%
          </button>
          <button class="btn btn-outline btn-success" @click="percentage = 0.5">
            50%
          </button>
          <button
            class="btn btn-outline btn-success"
            @click="showCustomPercentage = !showCustomPercentage"
          >
            Custom
          </button>
        </div>
        <input
          v-model="customPercentage"
          v-if="showCustomPercentage"
          type="number"
          class="input input-bordered w-full max-w-xs"
        />

        <!--Ende Number of People-->
      </div>
      <div class="card-body">
        <div>
          <p>tip amount: {{ tip }}</p>
        </div>
        <div>
          <p>total: {{ totalAmount }}</p>
        </div>
        <button class="btn btn-outline btn-success" @click="reset">
          Reset
        </button>
        <button class="btn btn-outline btn-success">switch currency</button>
      </div>
    </div>
  </div>
</template>

<style>
/** {
  border: 1px solid red;
}*/
</style>
