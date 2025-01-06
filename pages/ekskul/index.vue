<template>
  <div class="container">
    <h1 class="text-center py-3">Ekstrakurikuler</h1>
    <div class="row">
      <div
        v-for="(get, i) in eskul"
        :key="i"
        class="col-lg-4 d-flex justify-content-center pt-3 pb-3"
      >
        <div class="card bg-secondary" style="width: 18rem">
          <img :src="get.foto" class="card-img-top" alt="..." />

          <div class="card-body">
            <p class="card-text text-center text-white">
              {{ get.nama }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const eskul = ref([]);

const getData = async () => {
  const { data } = await supabase.from("ekskul").select(`*`);
  if (data) eskul.value = data;
};

onMounted(() => {
  getData();
});
</script>
