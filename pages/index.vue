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
      </div>
      <div class="card-body">
        <h2 class="card-title">rechts!</h2>
        <p text-right>Click the button to listen on Spotiwhy app.</p>
        <div class="card-actions justify-end">
          <button class="btn btn-primary">Listen</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
/* * {
  border: 1px solid red;
} */
</style>
