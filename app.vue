<template>
  <div class="flex justify-around space-x-4 p-4">
    <div
      v-for="(image, index) in cardImages"
      :key="image.id"
      class="bg-white shadow-lg rounded-lg overflow-hidden w-60 cursor-pointer"
      @click="increment(index)"
    >
      <img
        :src="image.url"
        alt="Card Image"
        class="w-full h-50 object-cover"
      />
      <div class="p-6 flex flex-col items-center justify-center text-center">
        <h2 class="text-xl font-semibold mb-2">{{ image.name }}</h2>
                <p>Count: {{ counts[index] }}</p>
      </div>
    </div>

    <!-- Popup Modal -->
    <div
      v-if="isPopupVisible"
      class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50"
    >
      <div class="bg-white p-4 rounded-lg shadow-lg text-center">
        <p class="text-lg font-semibold">Vote Success</p>
        <button
          @click="closePopup"
          class="mt-4 bg-blue-500 text-white px-4 py-2 rounded"
        >
          Close
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const counts = ref([0, 0]);
const isPopupVisible = ref(false);

const cardImages = [
  {
    id: "1",
    url: "https://www.lookbook.in.th/wp-content/uploads/2016/11/IMG_8486.jpg",
    name: "ลีเกด"
  },
  {
    id: "2",
    url: "https://f.ptcdn.info/419/084/000/lx4hefbviSH2KpkV1XD-o.jpg",
    name: "พั้นรักแมว"
  },
];

function increment(index) {
  counts.value[index]++;
  isPopupVisible.value = true;
}

function closePopup() {
  isPopupVisible.value = false;
}
</script>