<template>
  <div>
    <h1>Absen</h1>
    <NuxtLink to="/login">Login</NuxtLink>
    <NuxtLink to="/admin/tambah">tambah</NuxtLink>
    <table class="table">
      <thead>
        <tr>
          <th>#</th>
          <th>Tanggal</th>
          <th>Nama</th>
          <th>Keterangan</th>
          <th>Matpel</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="visitor in datas" :key="visitor.id">
          <td>{{ visitor.id }}</td>
          <td>{{ visitor.tanggal }}</td>
          <td>{{ visitor.nama }}</td>
          <td>{{ visitor.keterangan }}</td>
          <td>{{ visitor.matpel }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
// definePageMeta({
//   middleware: 'auth'
// })



const supabase = useSupabaseClient();
const datas = ref([]);

async function ambilData() {
  const { data, error } = await supabase.from("kehadiran").select();
  datas.value = data;
}

onMounted(() => {
  ambilData();
});
</script>
