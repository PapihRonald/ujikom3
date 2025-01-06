<template>
  <div class="container">
    <h1 class="text-center py-3">Galeri</h1>
    <div class="row">
      <div
        v-for="(get, i) in galeri"
        :key="i"
        class="col-lg-4 d-flex justify-content-center pt-3 pb-3"
      >
        <div class="card" style="width: 18rem">
          <img :src="get.foto" class="card-img-top" alt="..." />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const galeri = ref([]);

const getData = async () => {
  const { data } = await supabase.from("galeri").select(`*`);
  if (data) galeri.value = data;
};

onMounted(() => {
  getData();
});
</script>
