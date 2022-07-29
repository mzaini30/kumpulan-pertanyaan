<script lang="ts" setup="">
import acak from "../lib/acak";
// @ts-ignore
import listPertanyaan from "../pertanyaan.yml";
import { ref } from "vue";
import Info from "../komponen/info.vue";

const pertanyaan = ref(listPertanyaan);
const data = ref(acak(pertanyaan.value));
</script>

<template>
  <Info></Info>
  <div class="p-4 text-xl">
    {{ pertanyaan[0] }}
  </div>
  <a
    href="/"
    @click.prevent="pertanyaan = acak(pertanyaan)"
    class="block fixed bottom-0 right-0 p-2 text-sm underline"
    >acak</a
  >
</template>
