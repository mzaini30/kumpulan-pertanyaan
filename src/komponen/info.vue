<script setup="" lang="ts">
import latest from "latest-blogspot";
import { Ref, ref } from "vue";

type Hasil = {
  judul: string;
  link: string;
};
let hasil: Ref<Hasil> = ref({
  judul: "",
  link: "",
});

if (localStorage.info) {
  hasil.value = JSON.parse(localStorage.info);
}

async function init() {
  let data = await latest("https://blog.zenia.my.id", 1);
  hasil.value = data.blog[0];
  localStorage.info = JSON.stringify(hasil.value);
}
init();
</script>

<template>
  <!-- <p>{{ hasil.judul }}</p>
  <p>{{ hasil.link }}</p> -->
  <a
    class="bg-black text-white text-center text-sm p-3 block truncate"
    :href="hasil.link"
    >{{ hasil.judul }}
  </a>
</template>
