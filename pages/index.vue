<script setup>
import { Icon } from "@iconify/vue";
import { Camera, CameraResultType } from "@capacitor/camera";
import { useStore } from "~/store/store";
import { storeToRefs } from "pinia";

// useStore() and name handling:
const store = useStore();
const name = storeToRefs(store).name;

const newName = ref("");
function setName() {
  store.name = newName.value;
  newName.value = "";
}

// taking a picture and displaying it:
const imageUrl = ref(null);
async function takePic() {
  const image = await Camera.getPhoto({
    quality: 90,
    allowEditing: true,
    resultType: CameraResultType.Uri,
  });
  imageUrl.value = image.webPath;
}

definePageMeta({
  alias: "/home",
});
</script>

<template>
  <div flex justify-center items-center h="100vh">
    <div class="card lg:card-side bg-base-100 shadow-xl">
      <div class="card-body">
        <div class="form-control w-full max-w-xs">
          <label class="label">
            <span class="label-text">Bill</span>
          </label>
          <input
            type="text"
            placeholder="Type here"
            class="input input-bordered w-full max-w-xs"
            text-right
          />
        </div>
        <!-- Ende des Eingabefeldes -->
        <div class="form-control">
          <!-- Anfang Radio Button -->
          <label class="label cursor-pointer">
            <span class="label-text">5%</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <div class="form-control">
          <label class="label cursor-pointer">
            <span class="label-text">10%</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <div class="form-control">
          <label class="label cursor-pointer">
            <span class="label-text">15%</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <div class="form-control">
          <label class="label cursor-pointer">
            <span class="label-text">20%</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <div class="form-control">
          <label class="label cursor-pointer">
            <span class="label-text">25%</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <div class="form-control">
          <label class="label cursor-pointer">
            <span class="label-text">50%</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <div class="form-control">
          <label class="label cursor-pointer">
            <span class="label-text">Custom</span>
            <input
              type="radio"
              name="radio-10"
              class="radio checked:bg-blue-500"
              checked
            />
          </label>
        </div>
        <!-- Radio Button Ende -->
        <div class="form-control w-full max-w-xs">
          <!--Anfang Number of People-->
          <label class="label">
            <span class="label-text">Number of people</span>
          </label>
          <input
            type="text"
            placeholder="Type here"
            class="input input-bordered w-full max-w-xs"
          />
        </div>
        <!--Ende Number of People-->
      </div>
      <div class="card-body">
        <button class="btn">calculate tip</button>
        <div>
          <p>tip amount</p>
        </div>
        <div>
          <p>tip total</p>
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
