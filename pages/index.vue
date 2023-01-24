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
            <span class="label-text" text-base>Bill</span>
          </label>
          <input
            type="text"
            placeholder="Type here"
            class="input input-bordered w-full max-w-xs"
            text-right
          />
        </div>
        <!-- Ende des Eingabefeldes -->

        <button class="btn btn-secondary">5%</button>
        <button class="btn btn-secondary">10%</button>
        <button class="btn btn-secondary">15%</button>
        <button class="btn btn-secondary">20%</button>
        <button class="btn btn-secondary">25%</button>
        <button class="btn btn-secondary">50%</button>
        <button class="btn btn-secondary">Custom</button>

        <div class="form-control w-full max-w-xs">
          <!--Anfang Number of People-->
          <label class="label">
            <span class="label-text" text-base>Number of people</span>
          </label>
          <input
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
