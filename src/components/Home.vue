<template>
  <h1 class="font-extrabold text-3xl mb-6">Home</h1>

  <p class="mb-6">Name in store is: {{ name }}</p>

  <input
    v-model="newName"
    type="text"
    class="p-2 mr-4 border border-gray-600 rounded"
  />
  <button @click="saveName" class="text-white bg-indigo-600 p-2 rounded">
    Submit
  </button>
</template>

<script setup>
import { computed, ref } from 'vue';
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';

const router = useRouter();
const store = useStore();
const name = computed(() => {
  return store.state.user.name;
});
const newName = ref('');

function saveName() {
  store.dispatch('saveName', newName.value);
  newName.value = '';
  router.push('/about');
}
</script>
